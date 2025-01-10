Ticket servers are a cool way to create unique IDs. The idea is simple yet brilliant: they act as a centralized system for generating distributed primary keys. The folks at Flickr came up with this system, and it’s explained in their engineering blog: [Flickr's Engineering Blog Post](https://code.flickr.net/2010/02/08/ticket-servers-distributed-unique-primary-keys-on-the-cheap/).

![[Ticket Server.png]]
#### How does it work?

Here’s the gist:

- There’s a single database server called the **Ticket Server** that uses an _auto_increment_ feature to generate sequential IDs.
- These IDs are handed out to different systems that need unique identifiers.

#### Pros:

1. **Straightforward numeric IDs**: Simple, easy to use, and universally recognized.
2. **Simplicity**: Super easy to set up, making it a good fit for small to medium-sized apps.

#### Cons:

1. **Single point of failure**: If the ticket server crashes, everything relying on it comes to a halt.
    - Solution? Use multiple ticket servers. But that’s not as simple as it sounds because syncing data between them can get tricky.

This approach might not work for massive systems with super high demands, but for many applications, it’s a great start!