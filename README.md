# DomainLookout
This is a pre-release version of a Domain Monitoring tool built to allow companies to find newly registered domains that may be attackers trying to spoof your company

The currently the matching engine is basic and by making the sim value lower you can cut out noise but I am sure it will be missing domains, this is being worked on but so far it has been able to find a few true poisitives so I am happy that this is a valid POC and may be useful to some.

The current release was compiled for UNIX, other software versions will be coming once we get closer to an end product.

```

Usage: domainlookout [OPTIONS] --domain <DOMAIN>

Options:
  -d, --domain <DOMAIN>  The Domain you want to monitor
  -s, --sim <SIM>        Enter the value for simalirty matching The lower the closer the match needs to be to flag, Default = 3 [default: 3]
  -u, --uri <URI>        url for your tines Webhook to send found domains too [default: None]
  -h, --help             Print help
  -V, --version          Print version
  
```

When running the program you will get an output like this, the "Keep Connection Alive" section is keeping the connection to the stream open and counting the amount of domains processed since the last connection refresh, this is effectivly a heartbeat to insure that there is still a feed being recived. if this is 0 or the connection cannot open it will error

<img width="965" alt="image" src="https://user-images.githubusercontent.com/60553334/233292029-200c57c2-d44a-4e4e-8911-94ae3f0db4b6.png">

if you supply a Tines webhook, the domain will be fed into Tines on the body of the request and can be further processed from there

<img width="706" alt="image" src="https://user-images.githubusercontent.com/60553334/233292819-7167168f-db10-4bf4-8c3d-dcf25b10d3a4.png">
