# eCoin
The most basic crypto currency for you to use and learn the tech behind this event

### Prerequisites
You must have Sinatra installed
```bash
gem install sinatra
```

You must have a REST client. Preferably Postman

### Running on your own computer

Begin by cloning the repository
```bash
git clone https://github.com/EricChristensen/eCoin.git
```

Now fire up the server
```bash
ruby server.rb
```
The default be http://localhost:4576

Register your node for the network using the `register` endpoint
```
POST http://localhost:4576/register
{
  "your node name"
}
```
or
```
GET http://localhost:4576/register
```
The get should automatically retrieve your machine's IP address.

To see your own address use the `my_address` endpoint
```
GET http://localhost:4576/my_address
```

You can also unregister your node in the same way using the `unregister` endpoint
```
POST http://localhost:4576/unregister
{
  "your node name"
}
```
or
```
GET http://localhost:4576/unregister
```

Now that you have registered your node, others in the network are able to perform a transaction with you as well as use your copy of the chain to verify the longest chain. To be able to use other nodes who have registered with the network for verifying your own blockchain and to better exchange with them, use the `sync` endpoint.

```
GET http://localhost:4576/sync
```

This will give you the address of all nodes who have registered with the network. To view all of the addresses, use the `addressbook` endpoint.

```
GET http://localhost:4576/addressbook
```

To make a transaction with one of the people in your mailbox, use the `transaction` endpoint. You will need to provide, the sender's address, the receiver's address, and the ammount of money to send. To make a payment to someone, use your address as the `sender` and the person you are sending money as the `receiver`. To request a payment be made, put your address as the `receiver` and the person you are sending money to as the `sender`.

```
POST http://localhost:4576/transaction
{
  "sender" : "an address",
  "receiver" : "another address",
  "amount" : "amount of money you are sending or requesting"
}
```

To mine an eCoin use the `mine` endpoint
```
GET http://localhost:4576/mine
```

To see how much money you have in your account and your transaction history, use the `account` endpoint
```
GET http://localhost:4576/account
```

I think that is pretty much it for now.

You know what would be cool, getting an account with AWS or something as your computer. Using this as an email client or something. I think I will have to get an ever lasting node in a server in the cloud until I figure out how cryptos maintain their user list in a decentralized manner.
