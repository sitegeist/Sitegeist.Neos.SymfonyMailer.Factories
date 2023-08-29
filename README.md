# Sitegeist.Neos.SymfonyMailer.Factories

Factories to create SymfonyMailer and Mail instances in Neos.Flow

### Authors & Sponsors

* Martin Ficzel - ficzel@sitegeist.de

*The development and the public releases of this package is generously sponsored by our employer http://www.sitegeist.de.*

## Installation

Sitegeist.Neos.SymfonyMailer.Factories is available via packagist `composer require sitegeist/neos-symfonymailer-factories`.
We use semantic-versioning, so every breaking change will increase the major version number.

## Usage via PHP

The package provides two factory classes to create Mailers and Emails easily.

- `Sitegeist\Neos\SymfonyMailer\Factories\MailerFactory` with the method `createMailer` that will create a mailer for the specified dsn or the configured default dsn.
- `Sitegeist\Neos\SymfonyMailer\Factories\MailFactory` with the method `createMail` that will create a mail based on the provided arguments.

Example:
```php
use Sitegeist\Neos\SymfonyMailer\Factories\MailerFactory;
use Sitegeist\Neos\SymfonyMailer\Factories\MailFactor;

class MailController
{
    #[Flow\Inject]
    protected MailerFactory $mailerFactory;

    #[Flow\Inject]
    protected MailFactory $mailFactory;

    public function exampleAction()
    {
        $mailer = $this->mailerFactory->createMailer();
        $mail = $this->mailFactory->createMail(
            $subject,
            $recipient,
            $sender,
            $text,
            $html
        );
        $mailer->send($mail);
    }
```

## Configuration

The package allows to configure the dsn used by the mailer globally via settings. You can use the dsn specification as
it is documented by symfony here: https://symfony.com/doc/current/mailer.html#transport-setup

```yaml
Sitegeist:
  Neos:
    SymfonyMailer:
      dsn: 'sendmail://default'
```

## Contribution

We will gladly accept contributions. Please send us pull requests.

## License

See [LICENSE](./LICENSE)
