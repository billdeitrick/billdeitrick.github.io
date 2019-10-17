---
description: Additional resources for Azure Active Directory
type: talk
title: Azure Active Directory Notes and Resources
index: 2
---

## Helpful Azure AD Documentation

* [Dynamic Membership rules for Groups in Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership)
* [What is a device identity? (explains differences between Azure AD joined, registered, etc.)](https://docs.microsoft.com/en-us/azure/active-directory/devices/overview)

## Azure AD as IDP for G Suite

* [Tutorial: Azure Active Directory single sign-on (SSO) integration with G Suite](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/google-apps-tutorial)
* [Tutorial: Configure G Suite for automatic user provisioning](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/google-apps-provisioning-tutorial)
* [Set up single sign-on for managed Google Accounts using third-party Identity providers](https://support.google.com/a/answer/60224?hl=en&ref_topic=6348126)
* [Integrating Azure AD and G-Suite – Single Sign-On](https://journeyofthegeek.com/2018/01/24/integrating-azure-ad-and-google-apps-single-signon/)

### Azure AD/G Suite Notes

* Users must have an Exchange mailbox in order for the email attribute to be populated, since G Suite needs this attribute from the Identity Provider (IDP)
    * If the user doesn't have an Exchange mailbox, they won't be able to sign in to G Suite
* There are some settings you'll want to change to get the best experience on Chromebooks
    * See "[Configure SAML single sign-on for Chrome devices](https://support.google.com/chrome/a/answer/6060880)" for more details
    * We've found the best results by enabling Single Sign-on IdP Redirection (Device management > Chrome management > Device Settings > Single Sign-On IdP Redirection)

## Misc Links

* [Azure Active Directory is not Active Directory](https://samcogan.com/azure-active-directory-is-not-active-directory/)
