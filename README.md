# EJBCA-Installation

In the context of electronic signatures, PAdES, or PDF Advanced Electronic Signatures, is a set of rules and extensions applied to the PDF format and ISO 32000-1 to support Advanced Electronic Signatures (AdES). PAdES is important because it ensures that electronically signed documents remain valid and can be validated over a long period, possibly for years or even centuries. This meets the requirements of the European eIDAS regulation, which governs electronic identification and trust services for electronic transactions.

In this tutorial, I will guide you on how to use EJBCA as software to issue electronic certificates and Adobe Acrobat Reader as the software to perform electronic signing on specific documents.

1. Creating a Certificate Profile
Creating a certificate profile for issuing a CA that is one level below the Root CA. What is meant by a certificate profile? A certificate profile is a template used to define the format and purpose of a certificate.

To create a certificate profile, you can log into the EJBCA admin page and then select the certificate profiles option.

https://miro.medium.com/v2/resize:fit:1400/format:webp/1*nTOnXlReNyvSxMLAIF3piw.png
