sequenceDiagram

Client->>Controller: cancelOrder(id)

Controller->>OrderService: cancelOrder(id)

OrderService->>Repository: findById(id)

alt Order already shipped

OrderService-->>Controller: cancellationNotAllowed
Controller-->>Client: cannot cancel order

else Order can be cancelled

OrderService->>PaymentService: refundPayment()

OrderService->>Repository: updateStatus(CANCELLED)

OrderService-->>Controller: orderCancelled
Controller-->>Client: success


end
