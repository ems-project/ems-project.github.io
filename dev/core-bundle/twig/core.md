# Core

## emsco_log_[error | warning | notice]
Print flash message, usefull in post processing
```twig
{{ 'Example print error flash'|emsco_log_error }}
{{ 'Example print warning flash'|emsco_log_warning }}
{{ 'Example print notice flash'|emsco_log_notice }}
```
## emsco_generate_email
Generate an email and use [emsco_send_email](#emsco_send_email) for sending the email.
```twig
{% set mailBody %}
  <h1>Example email</h1>
  <p>example ...</p>
{% endset %}

{% set email = emsco_generate_email('test title') %}
{% do email.to('test@example.com').html(mailBody|format) %}
{% do emsco_send_email(email) %}
```

## emsco_send_email
Send an email generated with [emsco_generate_email](#emsco_generate_email).
Default value for from is `ems_core.from_email` and `%ems_core.name%` parameter.

```twig
{% set email = emsco_generate_email('example send') %}
{% do email.to('test@example.com').text('Body text') %}
{% do emsco_send_email(email) %}
```

## emsco_skip_notification
Can be used in notification in order to not send the notification and display a warning message.

```twig
{{ emsco_skip_notification() }}
```
The warning message can be defined:

```twig
{{ emsco_skip_notification('The title field is not provided, the request for publication can not be send.') }}
```

## emsco_form

Handle the current request with the form identified by its name. It allows to generate form in view, action or dashboard:

```twig
{% set form = emsco_form('user') %}
{% set formView = form.createView %}

{{ form_start(formView) }}
    {{ form_row(attribute(formView, 'user')) }}
    <div>
        <button type="submit" class="btm btn-primary">Filter</submit>
    </div>
{{ form(formView) }}

{% if form.valid %}
    {{ form.data.user|json_encode }}
{% endif %}
```