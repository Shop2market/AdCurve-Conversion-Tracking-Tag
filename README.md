# AdCurve Conversion Tracking Tag

The AdCurve Conversion Trackin Tag Template provides a way to quickly add AdCurve's conversion tracking tag to your website using Google Tag Manager's Community Template Gallery.

The tag can automatically grab the data it requires from the dataLayer using [Google's Enhanced Ecommerce](https://developers.google.com/tag-manager/enhanced-ecommerce) dataLayer model. However if this dataLayer model is not implemented on your website, you can manually configure each of the variables.

### Contents
- [Configuring your tag](#config)
- [Manual Variable Configuration](#manual)
  - [Order Details](#details)
  - [Order Products](#products)
---

## <a name="config"></a> Configuring your Tag

**AdCurve Shop Id:**\
Enter your AdCurve Shop Id. This can be found in the address bar when you viewing the AdCurve app (https://app.adcurve.com/shops/1234/...). If in doubt, just ask us. It's important that this id is correct, and the tag won't let you enter a value that is not number at least 3 digits long.

**Use Enhanced Ecommerce DataLayer:**\
This is checked by default and tells the tag to look for the [Purchase](https://developers.google.com/tag-manager/enhanced-ecommerce#purchases) action in the ecommerce object in the dataLayer. 

If you do not use the Enhanced Ecommerce dataLayer, or if your implementation does not conform to model in Google's documentation then you should uncheck the box and configur the variables manually

---

## <a name="manual"></a> Manual Variable Configuration

These two fields should be filled with Google Tag Manager variables that return a javascript object. If you're unsure how to set this up, please contact AdCurve support and we can assist you with it. 

### <a name="details"></a> Order Details
A javascript object representing the basic order information:

 |Key|Description|Type|
 |---|:---|---:|
 |id| order id|string|
 |revenue|Total order amount including tax and shipping|string|
 |tax|The tax amount of the order|string|
 |shipping|the shipping cost of the order|string|
 |coupon|any promotion or coupon code applied to the order|string|

**Example**
```javascript
{
  id: "#1005",
  revenue: "9.99",
  tax: "1.99",
  shipping: "1.95",
  coupon: "COUPON"
};
```
### <a name="products"></a> Order Products

An array of javascript objects representing the unique products sold in an order

 |Key|Description|Type|
 |---|:---|---:|
 |name|Product name/title|string|
 |id|Product Id / SKU|string|
 |brand|Brand / Manufacturer|string|
 |category|Product category, can be a delimited path |string|
 |quantity|Number of this item sold|string|
 |coupon|any promotion or coupon code applied to just this product|string|

**Example**
```javascript
[
  {
    name: "product one",
    id: "12345",
    brand: "Brand",
    category: "Category > Path",
    quantity: "1",
    coupon: ""
  },
  {
    name: "product two",
    id: "23456",
    brand: "Brand",
    category: "Category > Path",
    quantity: "1",
    coupon: ""
  },
]