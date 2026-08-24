# Reference
## Stores
<details><summary><code>client.stores.list() -> List&amp;lt;ListStoresResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns every store the authenticated user has access to, including summary counts for locations, cards, customers, and posters.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.stores().list();
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.stores.get(id) -> GetStoresResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns detailed information for a single store, including summary counts for its associated resources.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.stores().get(
    1,
    GetStoresRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `Integer` — Store ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.stores.update(id, request) -> UpdateStoresResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates the store's name or store_name. Use `store_name` for the public-facing name displayed to customers.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.stores().update(
    1,
    UpdateStoresRequest
        .builder()
        .account(
            UpdateStoresRequestAccount
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `Integer` — Store ID
    
</dd>
</dl>

<dl>
<dd>

**account:** `UpdateStoresRequestAccount` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Cards
<details><summary><code>client.cards.list(accountId) -> List&amp;lt;ListCardsResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns loyalty card templates for the specified store. By default, only
active (unarchived) cards are returned. Use the `scope` parameter to include
archived cards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.cards().list(
    1,
    ListCardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**scope:** `Optional<String>` — Filter cards by archive status. Default: active only.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.cards.create(accountId, request) -> CreateCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new loyalty stamp card template for the store. The card defines the
visual design (colours, icon, strip) and program rules (stamps required,
initial stamps).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.cards().create(
    1,
    CreateCardsRequest
        .builder()
        .card(
            CreateCardsRequestCard
                .builder()
                .name("name")
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**card:** `CreateCardsRequestCard` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.cards.get(accountId, id) -> GetCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single loyalty card template by ID, including reward and customer card counts.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.cards().get(
    1,
    1,
    GetCardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Card ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.cards.update(accountId, id, request) -> UpdateCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an existing loyalty card template. Only the provided attributes are changed.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.cards().update(
    1,
    1,
    UpdateCardsRequest
        .builder()
        .card(
            UpdateCardsRequestCard
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Card ID
    
</dd>
</dl>

<dl>
<dd>

**card:** `UpdateCardsRequestCard` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Customers
<details><summary><code>client.customers.list(accountId) -> ListCustomersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of customers for the store. Use the `search` parameter to filter
by name, email, phone, card code (barcode), or external reference ID. Alternatively, pass
`source` AND `external_id` together to perform an exact lookup by an external reference -
the response will contain at most one customer.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customers().list(
    1,
    ListCustomersRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**search:** `Optional<String>` — Search query to filter customers by name, email, phone, card code (barcode), or external reference ID
    
</dd>
</dl>

<dl>
<dd>

**source:** `Optional<String>` — External system slug (e.g. `square`, `shopify`). When combined with `external_id`, performs an exact lookup.
    
</dd>
</dl>

<dl>
<dd>

**externalId:** `Optional<String>` — External system's identifier for the customer. Must be combined with `source`.
    
</dd>
</dl>

<dl>
<dd>

**page:** `Optional<Integer>` — Page number (defaults to 1)
    
</dd>
</dl>

<dl>
<dd>

**items:** `Optional<Integer>` — Number of items per page
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customers.create(accountId, request) -> CreateCustomersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new customer for the store. Requires `first_name` and at least one of `email` or `phone`.
Optionally enroll the customer in a loyalty card by passing `card_id`, and trigger delivery of
card links (email/SMS) by passing `send_card_links`. When a card with initial stamps is assigned,
those stamps are automatically applied as a welcome bonus.

Pass `metadata` to attach arbitrary key/value data, and `external_references` to link the
customer to records in other systems (e.g. Square, Shopify). External references are upserted
by `(source, external_id)` so this endpoint is safe to call with the same references twice.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customers().create(
    1,
    CreateCustomersRequest
        .builder()
        .customer(
            CreateCustomersRequestCustomer
                .builder()
                .firstName("first_name")
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**cardId:** `Optional<Integer>` — Loyalty card ID to auto-enroll the customer in
    
</dd>
</dl>

<dl>
<dd>

**customer:** `CreateCustomersRequestCustomer` 
    
</dd>
</dl>

<dl>
<dd>

**sendCardLinks:** `Optional<Boolean>` — When true, sends the card links to the customer via email/SMS after enrollment. Note: even without this flag, the response includes `apple_wallet_url` and `google_wallet_url` in each customer card object so you can deliver them yourself.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customers.get(accountId, id) -> GetCustomersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns detailed information about a single customer, including all of their
enrolled loyalty cards with stamp progress and wallet pass URLs (`apple_wallet_url`
and `google_wallet_url`) for each card. Also includes `metadata` and
`external_references` so you can sync state with external systems.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customers().get(
    1,
    1,
    GetCustomersRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Customer ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customers.update(accountId, id, request) -> UpdateCustomersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an existing customer's details. To add stamps or redeem rewards, use the
customer cards endpoints instead.

`metadata` is shallow-merged into the existing metadata. `external_references` are upserted
by `(source, external_id)` - to remove a reference, omit it from subsequent calls and use
a separate `DELETE` workflow (not yet exposed via API; manage in dashboard for now).
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customers().update(
    1,
    1,
    UpdateCustomersRequest
        .builder()
        .customer(
            UpdateCustomersRequestCustomer
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Customer ID
    
</dd>
</dl>

<dl>
<dd>

**customer:** `UpdateCustomersRequestCustomer` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Customer Cards
<details><summary><code>client.customerCards.list(accountId, customerId) -> List&amp;lt;ListCustomerCardsResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all loyalty cards enrolled for a specific customer, including stamp progress,
status, wallet pass installation state, and wallet pass URLs (`apple_wallet_url` and
`google_wallet_url`) that you can use to let customers add their loyalty card to
Apple Wallet or Google Wallet from your own app or website.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customerCards().list(
    1,
    1,
    ListCustomerCardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**customerId:** `Integer` — Customer ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customerCards.get(accountId, customerId, id) -> GetCustomerCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns detailed information about a specific customer card, including stamp progress,
a list of rewards the customer has earned enough stamps to redeem, and wallet pass URLs
(`apple_wallet_url` and `google_wallet_url`) for adding the card to Apple Wallet or
Google Wallet.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customerCards().get(
    1,
    1,
    1,
    GetCustomerCardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**customerId:** `Integer` — Customer ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Customer card ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customerCards.redeem(accountId, customerId, id, request) -> RedeemCustomerCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Redeems a reward for a customer, deducting the required stamps from their card.
The customer must have enough stamps on this card to cover the reward's cost.
Triggers wallet pass updates and push notifications.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customerCards().redeem(
    1,
    1,
    1,
    RedeemCustomerCardsRequest
        .builder()
        .rewardId(1)
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**customerId:** `Integer` — Customer ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Customer card ID
    
</dd>
</dl>

<dl>
<dd>

**rewardId:** `Integer` — Reward ID to redeem
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.customerCards.stamp(accountId, customerId, id, request) -> StampCustomerCardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Adds stamps to a customer's loyalty card. Triggers ledger entries, wallet pass updates,
and push notifications. Pass `skip_notifications` to stamp silently.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.customerCards().stamp(
    1,
    1,
    1,
    StampCustomerCardsRequest
        .builder()
        .stamps(1)
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**customerId:** `Integer` — Customer ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Customer card ID
    
</dd>
</dl>

<dl>
<dd>

**skipNotifications:** `Optional<Boolean>` — When true, stamp changes bypass notifications
    
</dd>
</dl>

<dl>
<dd>

**stamps:** `Integer` — Number of stamps to add (e.g. 1, 3)
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Locations
<details><summary><code>client.locations.list(accountId) -> List&amp;lt;ListLocationsResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns every physical location belonging to the specified store.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.locations().list(
    1,
    ListLocationsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.locations.create(accountId, request) -> CreateLocationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new physical location for the store. The provided address is
automatically geocoded to latitude and longitude coordinates in the background.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.locations().create(
    1,
    CreateLocationsRequest
        .builder()
        .location(
            CreateLocationsRequestLocation
                .builder()
                .address("address")
                .name("name")
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**location:** `CreateLocationsRequestLocation` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.locations.get(accountId, id) -> GetLocationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single location by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.locations().get(
    1,
    1,
    GetLocationsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Location ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.locations.delete(accountId, id)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a location. This action cannot be undone.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.locations().delete(
    1,
    1,
    DeleteLocationsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Location ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.locations.update(accountId, id, request) -> UpdateLocationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an existing location. If the address is changed, it will be re-geocoded automatically.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.locations().update(
    1,
    1,
    UpdateLocationsRequest
        .builder()
        .location(
            UpdateLocationsRequestLocation
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Parent store ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Location ID
    
</dd>
</dl>

<dl>
<dd>

**location:** `UpdateLocationsRequestLocation` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Posters
<details><summary><code>client.posters.list(accountId) -> List&amp;lt;ListPostersResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all posters for the store. Optionally filter by card or active status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.posters().list(
    1,
    ListPostersRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**cardId:** `Optional<Integer>` — Filter posters belonging to a specific card
    
</dd>
</dl>

<dl>
<dd>

**active:** `Optional<String>` — When present, return only active posters
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posters.create(accountId, request) -> CreatePostersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new printable QR code poster for customer signup. The poster will automatically
generate a unique public signup URL and QR code. The `card_id` is required on create to
associate the poster with a loyalty card.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.posters().create(
    1,
    CreatePostersRequest
        .builder()
        .poster(
            CreatePostersRequestPoster
                .builder()
                .cardId(1)
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**poster:** `CreatePostersRequestPoster` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posters.get(accountId, id) -> GetPostersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single poster by ID, including generated signup and display URLs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.posters().get(
    1,
    1,
    GetPostersRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Poster ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posters.delete(accountId, id)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a poster. The public signup URL will stop working.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.posters().delete(
    1,
    1,
    DeletePostersRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Poster ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.posters.update(accountId, id, request) -> UpdatePostersResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an existing poster. The `card_id` cannot be changed after creation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.posters().update(
    1,
    1,
    UpdatePostersRequest
        .builder()
        .poster(
            UpdatePostersRequestPoster
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Poster ID
    
</dd>
</dl>

<dl>
<dd>

**poster:** `UpdatePostersRequestPoster` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Rewards
<details><summary><code>client.rewards.list(accountId) -> List&amp;lt;ListRewardsResponseItem&amp;gt;</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all rewards for the store. Optionally filter by card or active status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.rewards().list(
    1,
    ListRewardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**cardId:** `Optional<Integer>` — Filter rewards belonging to a specific card
    
</dd>
</dl>

<dl>
<dd>

**active:** `Optional<String>` — When present, return only active rewards
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.rewards.create(accountId, request) -> CreateRewardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new reward for a loyalty card. The card must belong to the same store.
The `card_id` is required on create but cannot be changed afterwards.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.rewards().create(
    1,
    CreateRewardsRequest
        .builder()
        .reward(
            CreateRewardsRequestReward
                .builder()
                .cardId(1)
                .name("name")
                .stampsRequired(1)
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**reward:** `CreateRewardsRequestReward` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.rewards.get(accountId, id) -> GetRewardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single reward by ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.rewards().get(
    1,
    1,
    GetRewardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Reward ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.rewards.delete(accountId, id)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a reward. This cannot be undone.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.rewards().delete(
    1,
    1,
    DeleteRewardsRequest
        .builder()
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Reward ID
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.rewards.update(accountId, id, request) -> UpdateRewardsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an existing reward. The `card_id` cannot be changed after creation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.rewards().update(
    1,
    1,
    UpdateRewardsRequest
        .builder()
        .reward(
            UpdateRewardsRequestReward
                .builder()
                .build()
        )
        .build()
);
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**accountId:** `Integer` — Store (account) ID
    
</dd>
</dl>

<dl>
<dd>

**id:** `Integer` — Reward ID
    
</dd>
</dl>

<dl>
<dd>

**reward:** `UpdateRewardsRequestReward` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Status
<details><summary><code>client.status.check() -> CheckStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the status of the API. No authentication required.

Every response from this API, including this one, carries `RateLimit-Limit`,
`RateLimit-Remaining`, `RateLimit-Reset` and `RateLimit-Policy`. Exceeding
the limit returns 429 with `Retry-After` in seconds.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```java
client.status().check();
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

