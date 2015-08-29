| Number            | Card type            |
| :---------------- | :------------------- |
| 4242424242424242  | Visa                 |
| 4012888888881881  | Visa                 |
| 4000056655665556  | Visa (debit)         |
| 5555555555554444  | MasterCard           |
| 5200828282828210  | MasterCard (debit)   |
| 5105105105105100  | MasterCard (prepaid) |
| 378282246310005   | American Express     |
| 371449635398431   | American Express     |
| 6011111111111117  | Discover             |
| 6011000990139424  | Discover             |
| 30569309025904    | Diners Club          |
| 38520000023237    | Diners Club          |
| 3530111333300000  | JCB                  |
| 3566002020360505  | JCB                  |

In addition, these cards will produce specific responses that are useful for testing different scenarios:

| Number            | Description
| :---------------- | :------------------- |
| 4000000000000077  | Charge will succeed and funds will be added directly to your available balance (bypassing your pending balance). |
| 4000000000000010  | With default account settings, charge will succeed but address_line1_check and address_zip_check will both fail. |
| 4000000000000028  | With default account settings, charge will succeed but address_line1_check will fail. |
| 4000000000000036  | With default account settings, charge will succeed but address_zip_check will fail. |
| 4000000000000044  | With default account settings, charge will succeed but address_zip_check and address_line1_check will both be unavailable. |
| 4000000000000101  | With default account settings, charge will succeed unless a CVC is entered, in which case cvc_check will fail and the charge will be declined. |
| 4000000000000341  | Attaching this card to a Customer object will succeed, but attempts to charge the customer will fail. |
| 4000000000000002  | Charge will be declined with a card_declined code. |
| 4100000000000019  | Charge will be declined with a card_declined code and a fraudulent reason. |
| 4000000000000127  | Charge will be declined with an incorrect_cvc code. |
| 4000000000000069  | Charge will be declined with an expired_card code. |
| 4000000000000119  | Charge will be declined with a processing_error code. |