# Solana Mobile Phone

As you may have observed, Solana has recently introduced its own mobile phone. In this section, We will outline essential details regarding the Solana Mobile Stack.

## What's in the Solana Mobile Stack?
The Solana Mobile Stack (SMS) is a collection of key technologies for building mobile applications that can interact with the Solana blockchain.

## Mobile Wallet Adapter​
Mobile Wallet Adapter (MWA) is a protocol specification for connecting mobile dApps to mobile Wallet Apps, enabling communication for Solana transaction and message signing.

dApps that implement MWA are able to connect to any compatible MWA Wallet App and request authorization, signing, and sending for transactions/messages.

Why this is important: Developers no longer need to build in support for each individual wallet, and instead can just integrate once and use a single unified API to be compatible with every compliant Solana wallet!

## Using the SDK
Solana Mobile maintains an official Mobile Wallet Adapter SDK that implements the protocol, originally written as a Android Kotlin/Java library.

The SDK is also ported other frameworks and is available for:

- React Native
- Flutter
- Unity
- Unreal Engine

## Seed Vault
The Seed Vault is a system service providing secure key custody to Wallet apps. By integrating with secure execution environments available on mobile devices (such as secure operating modes of the processor and/or secure auxiliary coprocessors), Seed Vault helps to keep your secrets safe, by moving them to the highest privileged environment available on the device. Your keys, seeds, and secrets never leave the secure execution environment, while UI components built into Android handle interaction with the user to provide a secure transaction signing experience to users.

## Solana dApp Store
The Solana dApp Store is an alternate app distribution system, well suited to distributing apps developed by the Solana ecosystem.
It will provide a distribution channel for apps that want to establish direct relationships with their customers, without other app stores’ rules restricting the relationship or seeking a large revenue share. The goal of the Solana dApp Store is to empower the Solana community to eventually play a key role in managing the contents of this app store.

## Solana Pay for Android
The Solana Pay protocol was developed independently of the Solana Mobile Stack, but combining payments with a mobile device is a natural fit for Solana Pay.
The Solana blockchain confirms transactions in less than a second and costs on average $0.0005, providing users a seamless experience with no intermediaries.
Businesses and developers can use Solana Pay to accept payments in SOL or any SPL token without intermediaries. It offers frictionless and portable integration options like payment links, pay now buttons or QR codes on your app, dApp, website, blog, and so much more.

## eCommerce Platform Integrations
Solana Labs has started a reference implementation for Shopify which you can see here to get a sense of how this might work.

Here are some of the top eCommerce platforms that they're looking to integrate to:

- WooCommerce
- Magento
- BigCommerce
- Wix
- Squarespace
