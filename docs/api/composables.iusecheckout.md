<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@shopware-pwa/composables](./composables.md) &gt; [IUseCheckout](./composables.iusecheckout.md)

## IUseCheckout interface

> This API is provided as a preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.
> 

interface for [useCheckout](./composables.usecheckout.md) composable

<b>Signature:</b>

```typescript
export interface IUseCheckout 
```

## Properties

|  Property | Type | Description |
|  --- | --- | --- |
|  [billingAddress](./composables.iusecheckout.billingaddress.md) | <code>Readonly&lt;Ref&lt;BillingAddress &#124; undefined&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [createOrder](./composables.iusecheckout.createorder.md) | <code>() =&gt; Promise&lt;Order&gt;</code> | <b><i>(BETA)</i></b> |
|  [getPaymentMethods](./composables.iusecheckout.getpaymentmethods.md) | <code>(options?: {</code><br/><code>        forceReload: boolean;</code><br/><code>    }) =&gt; Promise&lt;Readonly&lt;Ref&lt;readonly PaymentMethod[]&gt;&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [getShippingMethods](./composables.iusecheckout.getshippingmethods.md) | <code>(options?: {</code><br/><code>        forceReload: boolean;</code><br/><code>    }) =&gt; Promise&lt;Readonly&lt;Ref&lt;readonly ShippingMethod[]&gt;&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [guestOrderParams](./composables.iusecheckout.guestorderparams.md) | <code>Ref&lt;Readonly&lt;Partial&lt;GuestOrderParams &#124; null&gt;&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [isGuestOrder](./composables.iusecheckout.isguestorder.md) | <code>Readonly&lt;Ref&lt;boolean&gt;&gt;</code> | <b><i>(BETA)</i></b> Flag isGuestOrder is true when user is not logged in |
|  [paymentMethods](./composables.iusecheckout.paymentmethods.md) | <code>Readonly&lt;Ref&lt;readonly PaymentMethod[]&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [shippingAddress](./composables.iusecheckout.shippingaddress.md) | <code>Readonly&lt;Ref&lt;ShippingAddress &#124; undefined&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [shippingMethods](./composables.iusecheckout.shippingmethods.md) | <code>Readonly&lt;Ref&lt;readonly ShippingMethod[]&gt;&gt;</code> | <b><i>(BETA)</i></b> |
|  [updateGuestOrderParams](./composables.iusecheckout.updateguestorderparams.md) | <code>(params: Partial&lt;GuestOrderParams&gt;) =&gt; void</code> | <b><i>(BETA)</i></b> |
