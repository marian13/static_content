## Debugging

---

Custom config example for [Awesome Print](https://github.com/awesome-print/awesome_print) (1 / 2)

<div class="image">
  <img src="slides/convenient_service/7/debugging/standard_inspect.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/configs/awesome_print_inspect.rb" target="_blank"></a>
</div>

---

Custom config example for [Awesome Print](https://github.com/awesome-print/awesome_print) (2 / 2)

<div class="image">
  <img src="slides/convenient_service/7/debugging/awesome_print_inspect.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/configs/awesome_print_inspect.rb" target="_blank"></a>
</div>

---

Result has status checkers

<div class="image">
  <img src="slides/convenient_service/7/debugging/result_status_checkers.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Result has unsafe readers

<div class="image">
  <img src="slides/convenient_service/7/debugging/result_unsafe_readers.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Result has shorter unsafe readers

<div class="image">
  <img src="slides/convenient_service/7/debugging/result_short_unsafe_readers.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Result has parents 💥

<div class="image">
  <img src="slides/convenient_service/7/debugging/result_parents.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Result has access to its service instance

<div class="image">
  <img src="slides/convenient_service/7/debugging/result_service.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Service instance has access to its steps

<div class="image">
  <img src="slides/convenient_service/7/debugging/service_steps.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Step has access to its result

<div class="image">
  <img src="slides/convenient_service/7/debugging/step_result.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Step has access to its result via shorter syntax

<div class="image">
  <img src="slides/convenient_service/7/debugging/step_result_short_syntax.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Step has access to its underlying service result

<div class="image">
  <img src="slides/convenient_service/7/debugging/step_original_result.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Step has type queries

<div class="image">
  <img src="slides/convenient_service/7/debugging/step_type_queries.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Step has access to its input/output values

<div class="image">
  <img src="slides/convenient_service/7/debugging/step_io_values.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/read_file_content.rb" target="_blank"></a>
</div>

---

Service with exception example

<div class="image">
  <img src="slides/convenient_service/7/debugging/fake_exception_definition.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

Service result unhandled exception example

<div class="image">
  <img src="slides/convenient_service/7/debugging/fake_exception_raising.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/format.rb" target="_blank"></a>
</div>

---

Exception has access to its services 💥

<div class="image">
  <img src="slides/convenient_service/7/debugging/exception_services.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/service/plugins/collects_services_in_exception/middleware.rb" target="_blank"></a>
</div>

---

Exception has access to its service instances

<div class="image">
  <img src="slides/convenient_service/7/debugging/exception_service_instance.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

`RescuesResultUnhandledExceptions` (1 / 2)

<div class="image">
  <img src="slides/convenient_service/7/debugging/rescues_result_unhandled_exceptions.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/service/plugins/rescues_result_unhandled_exceptions/middleware.rb" target="_blank"></a>
</div>

---

`RescuesResultUnhandledExceptions` (2 / 2)

<div class="image">
  <img src="slides/convenient_service/7/debugging/failure_data_exception.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/service/plugins/rescues_result_unhandled_exceptions/middleware.rb" target="_blank"></a>
</div>
