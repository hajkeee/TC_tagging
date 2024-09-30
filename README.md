# E-Commerce dataLayer for GA4. Measurement Plan
| Event Name | Explanation | 
| ---------- | ----------- | 
| view_item_list  | To measure how many times item details are viewed, send a view_item event whenever a user views an item’s details screen. |
| view_item  | To measure how many times item details are viewed, send a view_item event whenever a user views an item’s details screen. |
| add_to_cart| To measure when someone adds merchandise to their shopping cart as a conversion. |
| remove_from_cart | To measure when a user removes an item from a cart. |
| begin_checkout  | Measure the first step in a checkout process by sending a begin_checkout event with one or more items defined with the relevant fields. A coupon can also be added at this stage to the entire order by adding it to the event or applied to a particular item by adding it to specific elements in the items array. | 
| add_shipping_info | When a user proceeds to the next step in the checkout process and adds shipping information. | 
| add_payment_info  | Send the add_payment_info event when a user submits their payment information. If applicable, include payment_type with this event for the chosen method of payment. |
| Purchase | Measure a purchase by sending a purchase event with one or more items defined with the relevant fields. The same apporach may be used for all events. Doceumentation in references section. |
| Refund | Measure a purchase by sending a purchase event with one or more items defined with the relevant fields |


# DataLayer Implementation



### Screenshot - view_item_list:
![Alt text](tc_view_item_list.png)

### Generate additional view_item_list when the user clicks on 'Load More'
![Alt text](tc_view_item.png)


### view_item_list
```html 
dataLayer.push({
   event: "view_item_list",
   ecommerce: {
      item_list_name: "Search",
      item_list_id: "s.3duz.4.m1orodl5",
      items: [
         {
            index: 0, // list position
            item_id: "LGW-CFU", // city - city
            item_name: "GB-GR", // country - country
            affiliation: "", 
            currency: "GBR", // currency
            price: 887.57, // item price
            item_brand: "Packages", // flight and hotel
            item_category: "RoundTrip", //
            item_category2: "International", // domestic or international
            item_category3: "|U2|A3|FR|", // airlines
            item_category4: "42",
            item_category5: "2",
            item_variant: "2|0|0|0", // 
            quantity: 1
         },
         {
            index: 1,
            item_id: "LTN-CFU",
            item_name: "GB-GR",
            affiliation: "",
            currency: "GBR",
            price: 926.58,
            item_brand: "Packages",
            item_category: "",
            item_category2: "",
            item_category3: "119610",
            item_category4: "42",
            item_category5: "2",
            item_variant: "2|0|0|0",
            quantity: 1
         }
      ]
   }
});

```


### Screenshot - view_item:
![Alt text](tc_view_item.png)


### view_item
```html 
dataLayer.push({
    event: "view_item",
    ecommerce: {
        item_list_name: "Search",
        item_list_id: "s.3duz.4.m1orodl5",
        items: [
            {
                item_id: "Laguna Holiday Resort", // hotel name
                item_name: "Laguna Holiday Resort", //hotel name
                affiliation: "", // 
                currency: "GBR", // currency
                price: 498.22, // hotel price
                item_brand: "Hotel", // 
                item_category: "",
                item_category2: "",
                item_category3: "110990",
                item_category4: "42",
                item_category5: "2",
                item_variant: "2|0",
                quantity: 1
            },
            {
                item_id: "CRF",
                item_name: "GR",
                affiliation: "",
                currency: "GBR",
                price: 1575.96,
                item_brand: "Flight",
                item_category: "RoundTrip",
                item_category2: "International",
                item_category3: "110990",
                item_category4: "42",
                item_category5: "2",
                item_variant: "2|0|0|0",
                quantity: 2
            }
        ]
    }
});

```


## Screenshot - add_to_cart:
![Alt text](tc_view_item.png)


### add_to_cart
```html 
dataLayer.push({
  event: "add_to_cart",
  value: 2074.18,
  ecommerce: {
    items: [
      {
        item_id: "CRF",
        item_name: "GB - GR",
        affiliation: "",
        currency: "GBR",
        index: 1,
        item_brand: "Flight",
        item_category: "MultiCity",
        item_category2: "International",
        item_category3: "U2|A3|FR", // Визначити категорію
        item_category4: "20", // Визначити категорію
        item_category5: "2", // Визначити категорію
        item_variant: "2|0|0|0",
        price: 576.24,
        quantity: 2
      },
      {
        item_id: "Sandy Beach Resort",
        item_name: "Sandy Beach Resort",
        affiliation: "",
        currency: "PLN",
        index: 2,
        item_brand: "Hotel",
        item_category3: "218640", // Визначити категорію
        item_category4: "20", // Визначити категорію
        item_category5: "2", // Визначити категорію
        item_category6: "4", // Визначити категорію
        item_variant: "2|0",
        price: 1276.92,
        quantity: 1
      }
    ]
  }
});

```




## begin_checkout
```html 
dataLayer.push({
  event: "begin_checkout",
    step: "extras" | "passenger_info" | "payment",
    value : 2,074.18
    "ecommerce": {
        "items": [
         {
            "item_id": "CRF",
            "item_name": "GB - GR",
            "affiliation": "",
            "currency": "GBR",
            "index": 1,
            "item_brand": "Flight",
            "item_category": "MultiCity",
            "item_category2": "International",
            "item_category3": "U2|A3|FR", ???????
            "item_category4": "20", ???????
            "item_category5": "2", ???????
            "item_variant": "2|0|0|0",
            "price": 576.24,
            "quantity": 2
         },
         {
            "item_id": "Sandy Beach Resort",
            "item_name": "Sandy Beach Resort",
            "affiliation": "",
            "currency": "PLN",
            "index": 2,
            "item_brand": "Hotel",
            "item_category3": "218640", ???????
            "item_category4": "20", ???????
            "item_category5": "2", ???????
            "item_category6": "4", ???????
            "item_variant": "2|0",
            "price": 1276.92,
            "quantity": 1
         }
      ]
   },

});
```

## Screenshot:
![Alt text](tc_view_item.png)

  
  ### Referenсes 
- [Data Layer](https://developers.google.com/tag-platform/devguides/datalayer?hl=en)
- [GA4 Events](https://developers.google.com/analytics/devguides/collection/ga4/reference/events)
- [GA4 Objects schema](https://support.google.com/analytics/answer/10119380?hl=en)
- [Google E-Commerce example Website](https://enhancedecommerce.appspot.com/)


