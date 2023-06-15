## Testing with Convenient Service

([RSpec](https://rspec.info))

---

Result matchers

| Matcher | Opposite matcher |
| - | - |
| [be_failure](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_failure.rb) | [be_not_failure](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_not_failure.rb) |
| [be_error](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_error.rb) | [be_not_error](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_not_error.rb) |
| [be_success](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_success.rb) | [be_not_success](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_not_success.rb) |
| | |

---

Result matchers chainings

| Matcher | Chainings |
| - | - |
| be_failure | [with(and)_data, with(and)_message](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_failure.rb) |
| be_error | [with(and)_message, with(and)_code](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_error.rb) |
| be_success | [with(and)_data](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/be_success.rb) |
| Common | [of_service, of_step, without_step, comparing_by](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/results/base.rb) |
| | |

---

Additional matchers

- [include_module](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/include_module.rb)

- [delegate_to 💥💥](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/delegate_to.rb)

- [call_chain_next](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/matchers/custom/call_chain_next.rb) (advanced)

---

Helpers

- [ignoring_error](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/helpers/custom/ignoring_error.rb)

- [stub_service](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/helpers/custom/stub_service.rb)

- [wrap_method](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/rspec/helpers/custom/wrap_method.rb) (advanced)

---

Simple test service (without steps)

<div class="image">
  <img src="slides/convenient_service/5/testing/simple_test_service.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

`be_success` matcher

<div class="image">
  <img src="slides/convenient_service/5/testing/be_success.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`be_failure` matcher

<div class="image">
  <img src="slides/convenient_service/5/testing/be_failure.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`be_failure` matcher with `with_data` chaining

<div class="image">
  <img src="slides/convenient_service/5/testing/be_failure_with_data.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`be_error` matcher

<div class="image">
  <img src="slides/convenient_service/5/testing/be_error.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`be_error` matcher with `with_message` chaining

<div class="image">
  <img src="slides/convenient_service/5/testing/be_error_with_message.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`without_step` chaining

<div class="image">
  <img src="slides/convenient_service/5/testing/without_step.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

`of_service` chaining

<div class="image">
  <img src="slides/convenient_service/5/testing/of_service.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>

---

More complex test service (with steps)

<div class="image">
  <img src="slides/convenient_service/5/testing/more_complex_test_service.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

`of_step` matcher with method

<div class="image">
  <img src="slides/convenient_service/5/testing/of_step_with_method.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/read_file_content_spec.rb" target="_blank"></a>
</div>

---

`of_step` matcher with service

<div class="image">
  <img src="slides/convenient_service/5/testing/of_step_with_service.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/read_file_content_spec.rb" target="_blank"></a>
</div>

---

`be_success` matcher with `with_data` chaining

<div class="image">
  <img src="slides/convenient_service/5/testing/be_success_with_data.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/read_file_content_spec.rb" target="_blank"></a>
</div>

---

Result matcher with multiple chainings

<div class="image">
  <img src="slides/convenient_service/5/testing/be_success_with_multiple_chainings.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/read_file_content_spec.rb" target="_blank"></a>
</div>

---

Partial Matching - `comparing_by("===")`

<div class="image">
  <img src="slides/convenient_service/5/testing/comparing_by.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/date_time/services/safe_parse_spec.rb" target="_blank"></a>
</div>

---

Partial Matching - RSpec expectations matchers

<div class="image">
  <img src="slides/convenient_service/5/testing/rspec_expectation_matchers.png">

  <a class="sticker" href="https://rspec.info/features/3-12/rspec-expectations/built-in-matchers" target="_blank"></a>
</div>

---

Partial Matching - RSpec mocks arguments matchers

<div class="image">
  <img src="slides/convenient_service/5/testing/rspec_mocks_arguments_matchers.png">

  <a class="sticker" href="https://rspec.info/features/3-12/rspec-mocks/setting-constraints/matching-arguments" target="_blank"></a>
</div>

---

`include_module` matcher

<div class="image">
  <img src="slides/convenient_service/5/testing/include_module.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists_spec.rb" target="_blank"></a>
</div>
