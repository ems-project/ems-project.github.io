# Security

## SAML (Single sign on)

For implementing an SSO with SAML protocol, we need a IDP (Identity Provider).
Enable a dev IDP see [dev-env](/getting-started/dev-env.md#identity-provider-idp-keycloak).

The current SSO implementation does only support the login. The logout on the IDP was not required.

We use the following library [onelogin/php-saml](https://github.com/SAML-Toolkits/php-saml/tree/4.1.0)

### Implementation

1) For forcing authentication on a route set default *_authenticated* to true.
   See [Routing](/dev/client-helper-bundle/routing.md) for more information.

2) Create a login and logout button in twig
   ```twig
        {% if app.user %}
            <h1>Welcome {{ app.user.userIdentifier }}</h1>
            <a href="{{ path("emsch_logout") }}">Logout</a>
        {% else %}
            <a href="{{ path("emsch_saml_login") }}">Login</a>
        {% endif %}
   ```
   
### Environment variables

| Name                      | Description                                                                         |
|---------------------------|-------------------------------------------------------------------------------------|
| EMSCH_SAML                | bool for enabling SAML                                                              |
| EMSCH_SAML_SP_ENTITY_ID   | unique name of our application known by the IDP                                     |
| EMSCH_SAML_SP_PUBLIC_KEY  | skeleton public key hosted `/saml/metadata`                                         |
| EMSCH_SAML_SP_PRIVATE_KEY | skeleton private key                                                                |
| EMSCH_SAML_IDP_ENTITY_ID  | client name in the IDP                                                              |
| EMSCH_SAML_IDP_PUBLIC_KEY | IDP public key                                                                      |
| EMSCH_SAML_IDP_SSO        | url to the IDP                                                                      |
| EMSCH_SAML_SECURITY       | overwrite [settings](https://github.com/SAML-Toolkits/php-saml/tree/4.0.0#settings) |