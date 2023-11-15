---
title: Setup
---

## Instalación de Git

Por favor consulte [esta sección de la plantilla de los talleres][workshop-setup]
para conocer más instrucciones de instalación de Git.

## Crear una cuenta de GitHub

Necesitarás una cuenta de [GitHub](https://github.com) para seguir esta lección.

1. Ve a <https://github.com> y sigue el enlace "Regístrate" en la parte superior derecha de la ventana.
2. Sigue las instrucciones para crear una cuenta.
3. Verifica tu dirección de correo electrónico con GitHub.
4. Configura la autenticación multifactor (ver más abajo).

### Autenticación multifactor

En 2023, GitHub introdujo el requisito de que todas las cuentas tuvieran configurada la 
[autenticación multifactor (2FA)](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) para mayor seguridad.
Existen varias opciones para configurar 2FA, que se resumen aquí:

1. Si ya utilizas una aplicación de autenticación, como [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en&co=GENIE.Platform%3DiOS&oco=0) o [Duo Mobile](https://duo.com/product/multi-factor-authentication-mfa/duo-mobile-app) en tu smartphone, por ejemplo, [añade GitHub a esa aplicación](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication#configuring-two-factor-authentication-using-a-totp-mobile-app).
2. Si tienes acceso a un smartphone pero aún no utilizas una aplicación de autenticación, instala una y [añade GitHub a la aplicación](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication#configuring-two-factor-authentication-using-a-totp-mobile-app).
3. Si no tienes acceso a un smartphone o no quieres instalar una aplicación de autenticación, tienes dos opciones:
   1. [configurar 2FA mediante mensaje de texto](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication#configuring-two-factor-authentication-using-text-messages)
      ([lista de países donde se admite la autenticación por SMS](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/countries-where-sms-authentication-is-supported)), o
   2. [utilizar una llave de seguridad de hardware](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication#configuring-two-factor-authentication-using-a-security-key)
      como [Youbikey](https://www.yubico.com/products/yubikey-5-overview/) o la [llave Titan de Google](https://store.google.com/us/product/titan_security_key?hl=en-US&pli=1).

La documentación de GitHub proporciona [más detalles sobre la configuración de 2FA](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication).

## Preparar el directorio de trabajo

Haremos nuestro trabajo en la carpeta `Desktop`. Por favor asegúrese de cambiar su directorio de trabajo con:

```bash
$ cd
$ cd Desktop
```

[workshop-setup]: https://carpentries.github.io/workshop-template/install_instructions/#git



