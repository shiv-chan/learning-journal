# Domain

## What is a domain?

Any computer that is connected to Internet is given a unique number. That number is called **IP address**.

With IP addresses, computers can be identified and communicate with the right ones.

However, IP addressed are not human-readable. Then, **domain names** exists to solve the problem.

| IP address     | domain name  |
| -------------- | ------------ |
| 208.65.153.238 | youtube.com  |
| 66.220.149.25  | facebook.com |
| 72.21.211.176  | amazon.com   |
| 173.0.84.3     | paypal.com   |

## Structure of domain names

![domain](https://user-images.githubusercontent.com/51708229/116645810-87f1ac00-a9b1-11eb-986b-3ad457b18d4b.png)

- Top level domain (TLD)

Generic TLDs are such as `.com`, `.org`, or `.net`. TLDs tell users the general purpose of the service.

Most don't require web services to meet any paticular criteria, but some TLDs need a clear policy showing the web service's purpose. For example, ccSLDs or `.gov`, `.edu`.

You can register whatever TLDs you want if it's approved.

- Secondary level domain (SLD)

SLD is the domain that is located to the left of the TLD.

This could be a name of a brand, a product, or a service.

- Country code second-level domains (ccSLD)

ccSLD represents a paticular language or country. This requires the service to be provided in a given language or hosted in a certain country.

ccSLD includes the following domain: `.us`, `.ca`, `.jp`.

## Owing a domain name

You never be able to buy a domain name. Instead of buying the one, you can register and pay for the right to use a domain name.

As long as you pay for it, you can contine to use your domain name. If you stop paying, that domain name will be availabe to anyone.

If you use a system with a built-in shell, you can check if the domain name is available or not with the command `whois`.

## What is DNS?

DNS is the acronym of Domain Network System.

This is the phonebook of the Internet. It can translate a domain name to IP address.

DNS request works in the following steps:

>1. Type mozilla.org in your browser's location bar.
>2. Your browser asks your computer if it already recognizes the IP address identified by this domain name (using a local DNS cache). If it does, the name is translated to the IP address and the browser negotiates contents with the web server. End of story.
>3. If your computer does not know which IP is behind the mozilla.org name, it goes on to ask a DNS server, whose job is precisely to tell your computer which IP address matches each registered domain name.
>4. Now that the computer knows the requested IP address, your browser can negotiate contents with the web server.

![スクリーンショット 2021-04-30 15 32 52](https://user-images.githubusercontent.com/51708229/116657467-62709c80-a9c9-11eb-9726-6056a8a7784f.png)

#### References

- [What is a Domain Name?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name)
- [What's in a Domain Name? All About Domain Levels](https://hover.blog/whats-a-domain-name-subdomain-top-level-domain/)
