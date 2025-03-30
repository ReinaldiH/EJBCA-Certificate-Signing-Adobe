# How to Create an Electronic Certificate in EJBCA and Sign in Adobe

In the context of electronic signatures, PAdES, or PDF Advanced Electronic Signatures, is a set of rules and extensions applied to the PDF format and ISO 32000-1 to support Advanced Electronic Signatures (AdES). PAdES is important because it ensures that electronically signed documents remain valid and can be validated over a long period, possibly for years or even centuries. This meets the requirements of the European eIDAS regulation, which governs electronic identification and trust services for electronic transactions.

In this tutorial, I will guide you on how to use EJBCA as software to issue electronic certificates and Adobe Acrobat Reader as the software to perform electronic signing on specific documents.

1. Creating a Certificate Profile
Creating a certificate profile for issuing a CA that is one level below the Root CA. What is meant by a certificate profile? A certificate profile is a template used to define the format and purpose of a certificate.

To create a certificate profile, you can log into the EJBCA admin page and then select the certificate profiles option.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*nTOnXlReNyvSxMLAIF3piw.png)

Clone the ROOTCA you have; once it appears in the list of certificate profiles, edit it first by following the settings in the image below

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*e6Ax6u2PZV09bpPvv_pVNg.png)

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*OG9iNwPVYV5yyLE6UToaag.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Gw__oAq3eZW4cbUsemPC6Q.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*9gLAszEV4y2dBCKNvA31Jw.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*dI-w9hzx7ustCSNISXi13A.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*ehPYfFZ-Vvc0v-cHUCPIHQ.png)  

2. Creating a Crypto Token

Before setting up a Certificate Authority (CA), the first step is to create a crypto token. In EJBCA, a crypto token is a secure storage area that holds cryptographic keys, either within a Hardware Security Module (HSM) or in a locally generated software keystore.

To create a crypto token, navigate to the EJBCA admin interface and select Crypto Tokens under the CA Functions menu. Click on Create New, enter a desired name for the crypto token, and ensure that the type is set to soft keystore.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*nbt9LElzja_MrgTYxE-ugg.png)  

Once the crypto token is created, the next step is to generate and add the necessary keys for the Root CA and CA. In this tutorial, I will create three keys for the Rei Coba Root CA. You can choose the encryption algorithm based on your preferences; in my case, I opted for RSA 4096.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*AhbpmiDGTzbsKo1rM7iYdQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*V_p_3vGfbwtWzPP54GeW6Q.png)  

3. Creating a Certificate Authority (CA)

In a CA hierarchy, the Root CA sits at the highest level. It is responsible for issuing and signing certificates for subordinate CAs, which will later issue certificates for end entities.

To create a CA, navigate to the Certification Authorities menu. Enter the desired Root CA name in the Add CA field, then click Create. You will then be redirected to configure the Root CA settings.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*u_3Zlap-AiTNAb7Zu3D4cA.png) 

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4Fc-nYo3J-o_mOAjuXNJVg.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*RVgp5ujsH85xAaqnMhDXJw.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*XGoS3D18TDipVM6vJnbHMA.png) 

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*897IlQE_x6U9U-kLdj5yMQ.png) 

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*R3nzI1n8npDMXgepvvKyEA.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*zuOtFa2MnODcS0rl4onvGQ.png)  

4. Creating an End Entity Profile

Now it's time to create a profile that will be used to issue certificates for end entities. An End Entity Profile is a template for the Subject Distinguished Name (DN) of an end entity, defining which fields are required, optional, or editable.

This section also includes information specific to each individual end entity. End Entity Profiles can also be used to restrict access to specific certificate profiles for issuing certificates to end entities.

To issue a certificate for an end entity, navigate to the EJBCA admin interface, go to the RA Functions menu, and select Add Entity.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*ai2mTgq2kUNAy2rjBAxCUQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*SOnnyP_Liek8qs0Eg2nCLg.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*j2CrqoXHunOc2akcmEd6RQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*OLTuVMb3na1a5-pTIYKV8w.png)  

5. Issuing a Certificate for a User

After adding an end entity, the next step is to issue its certificate. When an end entity is first added, its certificate is not yet issued. Its status will initially be "new" and will change to "generated" once the certificate is issued.

To issue a certificate, go back to the EJBCA home page and select "Create Keystore" under the Enroll section. In the authentication section, enter the previously registered username and password. In this example, we use the username "CobaRei".

Before proceeding, you can also visit the Public Web page.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1020/format:webp/1*wsaj1GLPxFhVmo4JSGFe8w.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*T2NJIPCrnJWmjIUmFyv_mQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Z3BndK1OSx5UNHq-l9rUHg.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CxAnynf77OjB7C1EQhEFXQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*lqpiEHUnVKY6v7AYigyojw.png)  

6. Electronically Signing a Document Using the Issued Certificate

Once the certificate has been issued, the next step is to sign a document using the certificate in Adobe Acrobat.

1. Open the .pdf file you want to sign in Adobe Acrobat.
2. Navigate to Tools → Certificates → Digitally Sign.
3. Click Configure New Digital ID.
4. Select Use a Digital ID from a file → Browse.
5. Enter the password for the Digital ID.
6. Click Add Digital ID, then select the Digital ID you just added.
7. Enter the password again and click Sign.


Your document is now digitally signed using the issued certificate.

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1244/format:webp/1*fQ9SLGwzhptuye1SGV4cnQ.png) 

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*1fomk8v6wYMhZzLMbfRnWQ.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*pxO7EJtiLLSfc4qeAyQ-vA.png)  

![EJBCA Picture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*tnSXRh2fSvM3bRib469HKw.png)  

![Gambar](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*k3bskNn1gx5C0onQHmtoCg.png)

![Gambar 1](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*k3bskNn1gx5C0onQHmtoCg.png)

![Gambar 2](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*TNcoi9xHa4s3CuIIJFQcnQ.png)

![Gambar 3](https://miro.medium.com/v2/resize:fit:1196/format:webp/1*JKtFqq-YzcCUVZwTOqFrxQ.png)

![Gambar 4](https://miro.medium.com/v2/resize:fit:1052/format:webp/1*iEURiTVGqX-ZLXdHOBBtpg.png)

![Gambar 5](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*T9Q17jgKTmRUgVArb7QvlQ.png)

![Gambar 6](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*8u6eBHGznfgYUcNl_Nrn3Q.png)

![Gambar 7](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*FY8A_YPv1rrIF-aCphORig.png)

![Gambar 8](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4lQ9zFBkSGQUpBze1t_DCQ.png)



7. Validating a Signed Document on Kominfo

To validate the signed document:

Open the Kominfo Certificate Authority website.

Upload the digitally signed document.

If the validation is successful, you should see a confirmation message similar to the one shown below.

![EJBCA Picture](https://raw.githubusercontent.com/ReinaldiH/EJBCA-Certificate-Signing-Adobe/main/1_Np2eAM_iUAG4ymxVanEP8A.webp)
