Gorilla Geek Mailer
===================

Install from nuget: https://www.nuget.org/packages/Gorilla.Mailer.SendGrid/

```bash
Install-Package Gorilla.Mailer.SendGrid
```

How to use
----------

```cs
IMailer mailer = Gorilla.Mailer.Providers.SendGridMailer("apikey");
var providerResultKey = await mailer.Send("Subject", "From", "To", "Body");
```

Template
--------

From String:
```cs
var template = MailerTemplate.CreateFromString("Your template here [TemplateVariable]");
template.Params.Add("TemplateVariable", "with variables");

var body = template.Render();
```

From File:
```cs
var template = MailerTemplate.CreateFromFileSystem("path-to-file");
```

From Namespace:
```cs
// Remember to change the file property 'Buld Action' to 'Embedded Resource'
var path = "MyApp.Templates.Email.html";
var template = MailerTemplate.CreateFromManifestResourceStream(path);
```