sequenceDiagram

Client->>Controller: placeOrder()

Controller->>OrderService: createOrder()

OrderService->>PaymentService: processPayment()

PaymentService->>PaymentGateway: charge()

alt Payment successful

PaymentGateway-->>PaymentService: success

PaymentService-->>OrderService: success

OrderService->>Repository: save(order)

opt Send confirmation email

OrderService->>EmailService: sendConfirmation()

end

OrderService-->>Controller: orderConfirmed

Controller-->>Client: success

else Payment failed

PaymentGateway-->>PaymentService: failed

PaymentService-->>OrderService: failed

OrderService-->>Controller: error

Controller-->>Client: payment failed


end
