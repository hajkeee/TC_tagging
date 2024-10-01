# E-Commerce dataLayer for GA4. Measurement Plan
| Event Name | Explanation | 
| ---------- | ----------- | 
| view_item_list  | To measure how often item details are viewed, send a view_item event whenever a user views an item’s details screen. |
| view_item  | To measure how often item details are viewed, send a view_item event whenever a user views an item’s details screen. |
| add_to_cart| To measure when someone adds merchandise to their shopping cart as a conversion. |
| remove_from_cart | To measure when a user removes an item from a cart. |
| begin_checkout  | Measure the first step in a checkout process by sending a begin_checkout event with one or more items defined with the relevant fields. A coupon can also be added at this stage to the entire order by adding it to the event or applied to a particular item by adding it to specific elements in the items array. | 
| add_shipping_info | When a user proceeds to the next step in the checkout process, shipping information is added. | 
| add_payment_info  | Send the add_payment_info event when a user submits their payment information. If applicable, include payment_type with this event for the chosen payment method. |
| Purchase | Measure a purchase by sending a purchase event with one or more items defined with the relevant fields. The same approach may be used for all events. Documentation in the references section. |
| Refund | Measure a purchase by sending a purchase event with one or more items defined with the relevant fields |


# DataLayer Implementation



### Screenshot - view_item_list - tag should be executed after user complited search action in service with parametrs in the datalayer:
![Alt text](tc_view_item_list.png)

### view_item_list
```html 
dataLayer.push({
   event: "view_item_list",
   ecommerce: {
      item_list_name: "Search", // how item list was generated
      item_list_id: "s.3duz.4.m1orodl5", // list_id
      items: [
         {
            index: 0, // item position
            item_id: "LGW-CFU", // city - city
            item_name: "GB-GR", // country - country
            affiliation: "", // if applicable
            currency: "GBR", // currency
            price: 887.57, // single item price
            item_brand: "Packages", // flight and hotel
            item_category: "RoundTrip", //
            item_category2: "International", // domestic or international
            item_category3: "|U2|A3|FR|", // airlines
            item_category4: "42", //comment
            item_category5: "2", // comment
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

### Generate additional view_item_list when the user clicks on 'Load More'
![Alt text](tc_load_more.png)


### view_item_list
```html 
dataLayer.push({
   event: "view_item_list",
   ecommerce: {
      item_list_name: "Search", // how item list was generated
      item_list_id: "s.3duz.4.m1orodl5", // list_id
      items: [
         {
            index: 13, // item position
            item_id: "LGW-CFU", // city - city
            item_name: "GB-GR", // country - country
            affiliation: "", // if applicable
            currency: "GBR", // currency
            price: 1039.38, // single item price
            item_brand: "Packages", // flight and hotel
            item_category: "RoundTrip", //
            item_category2: "International", // domestic or international
            item_category3: "|U2|A3|FR|", // airlines
            item_category4: "42", //comment
            item_category5: "2", // comment
            item_variant: "2|0|0|0", // 
            quantity: 1
         },
         {
            index: 14,
            item_id: "LTN-CFU",
            item_name: "GB-GR",
            affiliation: "",
            currency: "GBR",
            price: 696,
            item_brand: "Packages",
            item_category: "RoundTrip",
            item_category2: "International",
            item_category3: "|U2|A3|FR|",
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
### 

### view_item
```html 
dataLayer.push({
    event: "view_item",
    ecommerce: {
        item_list_name: "Search",
        item_list_id: "s.3duz.4.m1orodl5",
        items: [
            {
                item_id: "123213213", // hotel id - available in current implementation
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
                item_variant: "2|0", // number of guests
                quantity: 1
            },
            {
                item_id: "CRF", // target place - city
                item_name: "GR", // target place - country
                affiliation: "",
                currency: "GBR", 
                price: 1575.96,
                item_brand: "Flight", 
                item_category: "RoundTrip",
                item_category2: "International",
                item_category3: "110990",
                item_category4: "42",
                item_category5: "2",
                item_variant: "2|0|0|0", // number of tickets
                quantity: 1
            }
        ]
    }
});

```


## Screenshot - add_to_cart - tag should be executed after user selected all ancillaries and clicked "Continue". Please note, data final data should be updated based on selected ancillaries (transfer, luggage, car):
![Alt text](tc_add_to_card.png)


### add_to_cart
```html 
dataLayer.push({
  event: "add_to_cart",
  value: 1,378.72, // sum of all ancillaries, tickets, hotel
  ecommerce: {
    items: [
      {
        item_id: "CRF",
        item_name: "GB - GR",
        affiliation: "",
        currency: "GBR",
        item_brand: "Flight",
        item_category: "MultiCity",
        item_category2: "International",
        item_category3: "U2|A3|FR", // airlines
        item_category4: "20", // comment
        item_category5: "2", // comment
        item_variant: "2|0|0|0",
        price: 576.24,
        quantity: 1
      },
      {
        item_id: "Sandy Beach Resort",
        item_name: "Sandy Beach Resort",
        affiliation: "",
        currency: "GBR",
        item_brand: "Hotel",
        item_category3: "218640", 
        item_category4: "20", 
        item_category5: "2", 
        item_category6: "4", 
        item_variant: "2|0",
        price: 1276.92,
        quantity: 1
       },
       {
        item_id: "21321321", // Seat id if applicable 
        item_name: "1C Extra legroom/exit seat", // if applicable
        affiliation: "",
        currency: "GBR",
        item_brand: "Seat",
        item_category3: ", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "",
        price: 32.00,
        quantity: 1
       },
       {
        item_id: "2132131", // Luggage id
        item_name: "22kg Checked-in bag", // selected option - Checked-in bag|Sport equipment
        affiliation: "",
        currency: "GBR",
        item_brand: "Luggage", // if user selected additonal bags
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "22",
        price: 162.00, // based on selection
        quantity: 1
       },
       {
        item_id: "2132131", // transfer type id
        item_name: "Shared standard shuttle", // Shared standard shuttle| Private standard car| Private premium car| Private standard minibus| Private premium minibus
        affiliation: "",
        currency: "GBR",
        item_brand: "Transfer", // if user selected transfer
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "2|0",
        price: 20.54, // based on selection
        quantity: 1
       }.
        item_id: "2132131", // car id
        item_name: "Citroen C1, Volkswagen Up or similar - MDMRAA", // selected car
        affiliation: "",
        currency: "GBR",
        item_brand: "Car", // if user selected car
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "2|0",
        price: 68.64, // based on selection
        quantity: 1
      
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
      items: [
      {
        item_id: "CRF",
        item_name: "GB - GR",
        affiliation: "",
        currency: "GBR",
        item_brand: "Flight",
        item_category: "MultiCity",
        item_category2: "International",
        item_category3: "U2|A3|FR", // airlines
        item_category4: "20", // comment
        item_category5: "2", // comment
        item_variant: "2|0|0|0",
        price: 576.24,
        quantity: 1
      },
      {
        item_id: "Sandy Beach Resort",
        item_name: "Sandy Beach Resort",
        affiliation: "",
        currency: "GBR",
        item_brand: "Hotel",
        item_category3: "218640", 
        item_category4: "20", 
        item_category5: "2", 
        item_category6: "4", 
        item_variant: "2|0",
        price: 1276.92,
        quantity: 1
       },
       {
        item_id: "21321321", // Seat id if applicable 
        item_name: "1C Extra legroom/exit seat", // if applicable
        affiliation: "",
        currency: "GBR",
        item_brand: "Seat",
        item_category3: ", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "",
        price: 32.00,
        quantity: 1
       },
       {
        item_id: "2132131", // Luggage id
        item_name: "22kg Checked-in bag", // selected option - Checked-in bag|Sport equipment
        affiliation: "",
        currency: "GBR",
        item_brand: "Luggage", // if user selected additonal bags
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "22",
        price: 162.00, // based on selection
        quantity: 1
       },
       {
        item_id: "2132131", // transfer type id
        item_name: "Shared standard shuttle", // Shared standard shuttle| Private standard car| Private premium car| Private standard minibus| Private premium minibus
        affiliation: "",
        currency: "GBR",
        item_brand: "Transfer", // if user selected transfer
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "2|0",
        price: 20.54, // based on selection
        quantity: 1
       }.
        item_id: "2132131", // car id
        item_name: "Citroen C1, Volkswagen Up or similar - MDMRAA", // selected car
        affiliation: "",
        currency: "GBR",
        item_brand: "Car", // if user selected car
        item_category3: "", 
        item_category4: "", 
        item_category5: "", 
        item_category6: "", 
        item_variant: "2|0",
        price: 68.64, // based on selection
        quantity: 1
      
    ]
   },

});
```

## Screenshot:
![Alt text](tc_begin_checkout.png)

  
  ### Referenсes 
- [Data Layer](https://developers.google.com/tag-platform/devguides/datalayer?hl=en)
- [GA4 Events](https://developers.google.com/analytics/devguides/collection/ga4/reference/events)
- [GA4 Objects schema](https://support.google.com/analytics/answer/10119380?hl=en)
- [Google E-Commerce example Website](https://enhancedecommerce.appspot.com/)


