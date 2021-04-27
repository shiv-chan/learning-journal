# How the Internet Works

Internet is a wire that connects computers and transmits a variety of data and media among them.

When computers connect to the Internet, they can communicate.

Servers are also a special type of computers and they directly connect to the Internet. They have an own hard drive which include information or data such as a web page file.

Each server (computer) has a unique number which is called **IP address** or **Internet protocol address**. This helps indentify each server, and IP address looks like the following.

They are not written in a human-readable way, so it's also given a **domain name**.

| IP address     | domain name  |
| -------------- | ------------ |
| 208.65.153.238 | youtube.com  |
| 66.220.149.25  | facebook.com |
| 72.21.211.176  | amazon.com   |
| 173.0.84.3     | paypal.com   |

The Domain Name System (**DNS**) comes in here. DNS is the phonebook of the Internet. It can translate a domain name to IP address.

### Illustration of how the email is sent:

![Internet (1)](https://user-images.githubusercontent.com/51708229/116208671-1d0b5f80-a77c-11eb-996f-8d4924352123.png)

The devices such as our laptops or mobile phones are called **Client**, and the client indirectly connects to the Internet through Internet Servise Provider (ISP).

1. Client A accesses and log in to the gmail.com and composes the email.
2. Once A clicks the send button, gmail.com server sends the email to yahoo.com server.
3. After that, Client B accesses to yahoo.com server and retrieves the email.

Whenever the email or whatever data travels across the Internet, computers breaks the information into a smaller parts called **packets**.

When the packets reach to the destination, they are reassembled in the original order to make the informaiton.

![Internet (2)](https://user-images.githubusercontent.com/51708229/116213853-17fcdf00-a781-11eb-84d4-0f6c536d8488.png)

Each computer is connected to the tiny computer called **routers**.

The image above describes the journey of the packet that client A send going to facebook.com and coming back to client A.

1. Client A sends the information and it becomes a packet.
2. The packet first reaches "red" router and it adds the packet its own IP address.
3. As the packet reaches each computer (ISP, "gray" router, "green" router, facebook.com in this case.), each computer adds its own IP address. It becomes like a layer.
4. When the packets starts to go back to Client A from facebook.com, each computer identifies the IP address and leads the packets the right direction.

#### Reference

- [How the Internet Works in 5 Minutes](https://youtu.be/7_LPdttKXPc)
- [How does the Internet work?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
- [How Does the Internet Work: A Step-by-Step Pictorial](https://www.hp.com/us-en/shop/tech-takes/how-does-the-internet-work#:~:text=It%20works%20by%20using%20a,where%20you're%20using%20it.)
- [What is a DNS server](https://www.cloudflare.com/learning/dns/what-is-a-dns-server/)
