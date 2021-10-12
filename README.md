# RazorPay-Core


[!["Buy Me A Coffee"](https://cdn.buymeacoffee.com/assets/img/home-page-v3/bmc-new-logo.png)](https://www.buymeacoffee.com/varunteja)

Razorpay .Core SDK
=================  
Razorpay client .NET Api. The api follows the following practices
* Namespaced under Razorpay.Api .
* Client throws exceptions instead of returning errors.
* Options are passed as Dictionary instead of multiple arguments wherever possible.
* All request and responses are communicated over JSON.
* A minimum of .Net 4.0 is required.

Installation
--------
If you are using nuget package manager:

`
Install-Package RazorPay.Core
`
Usage
-----
### Initialize
```cs
RazorpayClient client = new RazorpayClient(key, secret); 
```
                          OR
```cs
RazorpayClient client = new RazorpayClient(baseUrl, key, secret); 
```

### Get Payments
```cs
Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("from", startTime); // start time is a unix timestamp, you can get unix timestamp using                                // Utils.ToUnixTimestamp  method

List<Payment> payments = client.Payment.All(options);
```


### Get Payment using Id
```cs
Payment payment = client.Payment.Fetch(id);
```

### Capture a payment
```cs
Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("amount", amountToBeCaptured); 

Payment payment = payment.Capture(options);
```

### Refund a payment
```cs
Refund refund = payment.createRefund();
```

### Fetch All Refunds for a payment
```cs
List<Refund> refunds = payment.getAllRefunds();
```

### Fetch One Refund for a payment using refund id
```cs
Refund refund = payment.fetchRefund(id);
```

### Accessing the payment attributes
```cs
paymentAmount = payment["amount"];
```

### Create an order
```cs
Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("amount", TransactionAmount); 
options.Add("currency", "INR"); 
options.Add("receipt", "MerchantTransactionId"); 
options.Add("payment_capture", 1); 

Order order = Order.Create(options);
```

### Create a customer
```cs
Dictionary<string, object> options = new Dictionary<string,object>();

options.Add("name", "customer name"); 
options.Add("contact", "9999999999"); 
options.Add("email", "foo@example.com"); 
options.Add("fail_existing", 0); 

Customer customer = Customer.Create(options);
```
