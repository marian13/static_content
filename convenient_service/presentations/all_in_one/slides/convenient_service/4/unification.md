## Unification by Convenient Service

---

## Clean Code

When (by [marian13](https://github.com/marian13) custom definition):

- The author's intention is obvious
- In less than 10 minutes
- With minimal context
- Without diving into implementation
- Without running that code

---

Service names start with a verb (1 / 2)

```ruby
class ReadFileContent
  # ...
end

class StripComments
  # ...
end

class ParseContent
  # ...
end

class FormatHeader
  # ...
end

class FormatBody
  # ...
end

class MergeSections
  # ...
end
```

---

Service names start with a verb (2 / 2)

<div class="image">
  <img src="slides/convenient_service/4/unification/service_names.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/examples/standard/gemfile/services" target="_blank"></a>
</div>

---

Services have only one entry method - `result` (1 / 2)

```ruby
class AssertFileExists
  # ...

  def result
    # ...
  end
end

class RunShellCommand
  # ...

  def result
    # ...
  end
end

class AssertNpmPackageAvailable
  # ...

  def result
    # ...
  end
end
```

---

Services have only one entry method - `result` (2 / 2)

<div class="image">
  <img src="slides/convenient_service/4/unification/service_result.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/cowsay/services/build_cow.rb" target="_blank"></a>
</div>

---

Service results are called explicitly

```ruby
##
# Via class method:
# - Preferred way.
#
result = RunShellCommand.result(command: "ls -a")
```

```ruby
##
# Via instance method:
# - Useful for delaying service result calculation.
#
service = RunShellCommand.new(command: "ls -a")

result = service.result
```

---

Results return [JSend](https://github.com/omniti-labs/jsend/blob/master/README.md)-inspired structs (1 / 2)

```ruby
class AssertFileExists
  # ...

  def result
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    if !::File.exist?(path)
      return error("File with path `#{path}` does NOT exist")
    end

    success
  end
end
```

---

Results return [JSend](https://github.com/omniti-labs/jsend/blob/master/README.md)-inspired structs (2 / 2)

<div class="image">
  <img src="slides/convenient_service/4/unification/jsend_result.png">

  <a class="sticker" href="https://github.com/omniti-labs/jsend/blob/master/README.md" target="_blank"></a>
</div>

---

`success` - when service goal is achieved

```ruby [1,12]
class AssertFileExists
  # ...

  def result
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    if !::File.exist?(path)
      return error("File with path `#{path}` does NOT exist")
    end

    success
  end
end
```

(for `AssertFileExists` - when file actually exists)

---

`error` - when service goal is NOT achieved

```ruby [1,9]
class AssertFileExists
  # ...

  def result
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    if !::File.exist?(path)
      return error("File with path `#{path}` does NOT exist")
    end

    success
  end
end
```

(for `AssertFileExists` - when file does NOT exist)

---

`failure` - when service goal is NOT achieved due to
invalid input

```ruby [1,5-6]
class AssertFileExists
  # ...

  def result
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    if !::File.exist?(path)
      return error("File with path `#{path}` does NOT exist")
    end

    success
  end
end
```

(for `AssertFileExists` - when path is NOT present)

---

Results are ducks

<div class="image">
  <img src="slides/convenient_service/4/unification/results_are_ducks.png">

  <a class="sticker" href="https://marian13.github.io/convenient_service_docs/basics/results_are_ducks" target="_blank"></a>
</div>

---

Services have only one `success` case

```ruby
class AssertFileExists
  # ...

  def result
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    if !::File.exist?(path)
      return error("File with path `#{path}` does NOT exist")
    end

    success
  end
end
```

---

<span data-tippy-content="It is the developer's responsibility to predict reasonable exceptional cases and to handle them properly">Services have no unhandled exceptions</span>

<div class="image">
  <img src="slides/convenient_service/4/unification/service_without_exceptions.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/date_time/services/safe_parse.rb" target="_blank"></a>
</div>

---

## Tell, Don't Ask

<div class="image">
  <img src="slides/convenient_service/4/unification/tell_dont_ask.png">

  <a class="sticker" href="https://thoughtbot.com/blog/tell-dont-ask" target="_blank"></a>
</div>

---

## <span data-tippy-content="Actually only a small subset of Railway Oriented Programming">Railway Oriented Programming</span>

<div class="image">
  <img src="slides/convenient_service/4/unification/transparent_long_connected_railway.png">

  <a class="sticker" href="https://blog.logrocket.com/what-is-railway-oriented-programming" target="_blank"></a>
</div>

<div class="image">
  <img src="slides/convenient_service/4/unification/transparent_long_connected_railway_with_blocks.png">

  <a class="sticker" href="https://fsharpforfunandprofit.com/posts/recipe-part2" target="_blank"></a>
</div>

---

Complex services are composed of sequences of steps

```ruby
class ReadFileContent
  include ConvenientService::Standard::Config

  attr_reader :path

  step :validate_path
  step AssertFileExists, in: :path
  step AssertFileNotEmpty, in: :path
  step :result, in: :path, out: :content

  def initialize(path:)
    @path = path
  end

  def result
    success(content: ::File.read(path))
  end

  private

  def validate_path
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    success
  end
end
```

---

Steps can be methods.

```ruby [1,6,9,15-17,21-26]
class ReadFileContent
  include ConvenientService::Standard::Config

  attr_reader :path

  step :validate_path
  step AssertFileExists, in: :path
  step AssertFileNotEmpty, in: :path
  step :result, in: :path, out: :content

  def initialize(path:)
    @path = path
  end

  def result
    success(content: ::File.read(path))
  end

  private

  def validate_path
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    success
  end
end
```

---

Steps can be services.

```ruby [1,7-8]
class ReadFileContent
  include ConvenientService::Standard::Config

  attr_reader :path

  step :validate_path
  step AssertFileExists, in: :path
  step AssertFileNotEmpty, in: :path
  step :result, in: :path, out: :content

  def initialize(path:)
    @path = path
  end

  def result
    success(content: ::File.read(path))
  end

  private

  def validate_path
    return failure(path: "Path is `nil`") if path.nil?
    return failure(path: "Path is empty") if path.empty?

    success
  end
end
```

---

<span data-tippy-content="It is possible to figure out any service algorithm in the reproducable manner">Services with steps are readable in the same way</span>

```ruby
# 1. In order to read file content
class ReadFileContent
  # ...

  # 2. It is nessesary:

  # 3. To validate path.
  step :validate_path

  # 3. To assert that file exists.
  step AssertFileExists, in: :path

  # 4. To assert that file is NOT empty.
  step AssertFileNotEmpty, in: :path

  # 5. To finally perform the actual reading of file content.
  step :result, in: :path, out: :content

  def result
    success(content: ::File.read(path))
  end

  # ...
end
```

---

All steps are successful - service returns its last step

<div class="image">
  <img src="slides/convenient_service/4/unification/last_step_result.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Any step is not successful - service returns that step

<div class="image">
  <img src="slides/convenient_service/4/unification/not_successful_step_result.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Not successful step results are bubbled to the top

<div class="image">
  <img src="slides/convenient_service/4/unification/not_successful_step_result_bubbling.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Service with a lot of steps example (1 / 2)

```ruby
class FormatGemfile
  include ConvenientService::Standard::Config

  attr_reader :path

  step ReadFileContent,
    in: :path,
    out: :content

  step StripComments,
    in: :content,
    out: :content_without_comments

  step ParseContent,
    in: {content: :content_without_comments},
    out: :parsed_content

  step FormatHeader,
    in: :parsed_content,
    out: {formatted_content: :formatted_header_content}

  step FormatBody,
    in: :parsed_content,
    out: {formatted_content: :formatted_body_content}

  step MergeSections,
    in: [
      {header: :formatted_header_content},
      {body: :formatted_body_content}
    ],
    out: :merged_sections

  step ReplaceFileContent,
    in: [
      :path,
      {content: :merged_sections}
    ]

  def initialize(path:)
    @path = path
  end
end
```

---

Service with a lot of steps example (2 / 2)

```ruby
class PrepareRequestParams
  include ConvenientService::Standard::Config

  attr_reader :request

  step ExtractParamsFromPath,
    in: [:request, {pattern: raw(/^\/rules\/(?<id>\d+)\.(?<format>\w+)$/)}],
    out: {params: :params_from_path}

  step ExtractParamsFromBody,
    in: :request,
    out: {params: :params_from_body}

  step MergeParams,
    in: [:params_from_path, :params_from_body],
    out: :params

  step LogRequestParams,
    in: [:request, :params, tag: raw("Uncasted")]

  step FilterOutUnpermittedParams,
    in: [:params, {permitted_keys: raw([:id, :format, :title, :description, :tags, :sources])}],
    out: reassign(:params)

  step ApplyDefaultParamValues,
    in: [:params, defaults: raw({format: "json", tags: [], sources: []})],
    out: reassign(:params)

  step ValidateUncastedParams,
    in: :params

  step CastParams,
    in: :params,
    out: [:original_params, {casted_params: reassign(:params)}]

  step LogRequestParams,
    in: [:request, :params, tag: raw("Casted")]

  step ValidateCastedParams,
    in: [:original_params, {casted_params: :params}]

  step :result,
    in: :params,
    out: reassign(:params)

  def initialize(request:)
    @request = request
  end

  def result
    success(params: params)
  end
end
```

---

Step definitions are converted to the service calls <br> by the rules defined in the [Translation table](https://marian13.github.io/convenient_service_docs/basics/step_to_result_translation_table)

<div class="image">
  <img src="slides/convenient_service/4/unification/translation_table.png">

  <a class="sticker" href="https://marian13.github.io/convenient_service_docs/basics/step_to_result_translation_table" target="_blank"></a>
</div>

---

Steps can be tried by `try` option

<div class="image">
  <img src="slides/convenient_service/4/unification/try_step.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/run_shell_command.rb" target="_blank"></a>
</div>

---

`try` step option works when service has `try_result`

<div class="image">
  <img src="slides/convenient_service/4/unification/try_result.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/print_shell_command.rb" target="_blank"></a>
</div>

---

`try_result` is called when `result` is NOT successful

<div class="image">
  <img src="slides/convenient_service/4/unification/try_result_when_not_successful_result.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/service/plugins/can_have_steps/entities/step/plugins/can_be_tried/result/middleware.rb" target="_blank"></a>
</div>
