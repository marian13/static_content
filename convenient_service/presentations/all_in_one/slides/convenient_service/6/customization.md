## Customization in Convenient Service 💥💥

---

Plugin - combo of Concern or/and Middlewares

<div class="image">
  <img src="slides/convenient_service/6/customization/plugin.png">

  <a class="sticker" href="https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/common/plugins/caches_constructor_params" target="_blank"></a>
</div>

---

Concern - instance or/and class methods as modules

<div class="image">
  <img src="slides/convenient_service/6/customization/concern.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/common/plugins/has_callbacks/concern.rb" target="_blank"></a>
</div>

---

Middleware - method pre or/and post processor

<div class="image">
  <img src="slides/convenient_service/6/customization/middleware.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/common/plugins/caches_return_value/middleware.rb" target="_blank"></a>
</div>

---

Config - stack of plugins to apply

<div class="image">
  <img src="slides/convenient_service/6/customization/config.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/configs/standard.rb">
  </a>
</div>

---

Resources

<div class="image">
  <img src="slides/convenient_service/6/customization/resources.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/tree/main/lib/convenient_service" target="_blank"></a>
</div>

---

Plugins are grouped by resources

- [Common](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/common/plugins) plugins (applicable to any resource)

- [Service](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins) plugins

- [Result](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/has_result/entities/result/plugins) plugins

- [Status](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/has_result/entities/result/plugins/has_j_send_status_and_attributes/entities/status/plugins), [Data](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/has_result/entities/result/plugins/has_j_send_status_and_attributes/entities/data/plugins), [Message](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/has_result/entities/result/plugins/has_j_send_status_and_attributes/entities/message/plugins), [Code](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/has_result/entities/result/plugins/has_j_send_status_and_attributes/entities/code/plugins) plugins

- [Step](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/service/plugins/can_have_steps/entities/step/plugins) plugins

- [Internals](https://github.com/marian13/convenient_service/tree/main/lib/convenient_service/common/plugins/has_internals/entities/internals/plugins) plugins (advanced)

---

Sub resource config example

<div class="image">
  <img src="slides/convenient_service/6/customization/sub_resource_config.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/configs/standard.rb" target="_blank"></a>
</div>

---

Standard config - [ConvenientService::Standard::Config](https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/configs/standard.rb)

<div class="image">
  <img src="slides/convenient_service/6/customization/standard_config_example.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/standard/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

Custom config example for Rails (1 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/rails_config.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/rails/gemfile/rails_service/config.rb" target="_blank"></a>
</div>

---

Custom config example for Rails (2 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/rails_config_service.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/rails/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

Custom config example for DRY (1 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/dry_config.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/dry/gemfile/dry_service/config.rb" target="_blank"></a>
</div>

---

Custom config example for DRY (2 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/dry_config_service.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/examples/dry/gemfile/services/assert_file_exists.rb" target="_blank"></a>
</div>

---

Non Standard Plugins are not preloaded

<div class="image">
  <img src="slides/convenient_service/6/customization/builtin_dependencies.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/dependencies.rb" target="_blank"></a>
</div>

---

User checks gems for plugins with external deps

<div class="image">
  <img src="slides/convenient_service/6/customization/external_dependencies.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/dependencies.rb" target="_blank"></a>
</div>

---

Config modification for a single service

<div class="image">
  <img src="slides/convenient_service/6/customization/single_service_config.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/core/entities/config/entities/method_middlewares/entities/stack.rb" target="_blank"></a>
</div>

---

Config modification options

<div class="image">
  <img src="slides/convenient_service/6/customization/stack_options.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/core/entities/config/entities/method_middlewares/entities/stack.rb" target="_blank"></a>
</div>

---

Middleware with params (1 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/middleware_with_params.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/spec/lib/convenient_service/service/plugins/rescues_result_unhandled_exceptions/middleware_spec.rb" target="_blank"></a>
</div>

---

Middleware with params (2 / 2)

<div class="image">
  <img src="slides/convenient_service/6/customization/middleware_with_params_access.png" />

  <a class="sticker" href="https://github.com/marian13/convenient_service/blob/main/lib/convenient_service/service/plugins/rescues_result_unhandled_exceptions/middleware.rb" target="_blank"></a>
</div>
