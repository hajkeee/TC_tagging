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
  
| Event Name | Explanation | 
| Purchase | Measure a purchase by sending a purchase event with one or more items defined with the relevant fields. The same apporach may be used for all events. Documentation in references section. |

## DataLayer Implementation Examples:
## view_item_list
```html 
dataLayer.push({
   event: "view_item_list",
   "ecommerce": {
      "item_list_name": "LO_CRF",
      "items": [
         {
            "index": 0,
            "item_id": "CRF",
            "item_name": "GR",
            "affiliation": "",
            "currency": "GBR",
            "price": 396,
            "item_brand": "Hotel",
            "item_category": "",
            "item_category2": "",
            "item_category3": "110990",
            "item_category4": "42",
            "item_category5": "2",
            "item_variant": "2|0|0|0",
            "quantity": 1
         },
         {
            "index": 1,
            "item_id": "CRF",
            "item_name": "GR",
            "affiliation": "",
            "currency": "GBR",
            "price": 323,
            "item_brand": "Hotel",
            "item_category": "",
            "item_category2": "",
            "item_category3": "119610",
            "item_category4": "42",
            "item_category5": "2",
            "item_variant": "2|0|0|0",
            "quantity": 1
         },
});
```

## Screenshot:
![Alt text](tc_view_item_list.png)


## view_item
```html 
dataLayer.push({
  event: "view_item", 
        "items": [
         {
            "index": 0,
            "item_id": "CRF",
            "item_name": "GR",
            "affiliation": "",
            "currency": "GBR",
            "price": 396,
            "item_brand": "Hotel",
            "item_category": "",
            "item_category2": "",
            "item_category3": "110990",
            "item_category4": "42",
            "item_category5": "2",
            "item_variant": "2|0|0|0",
            "quantity": 1
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


