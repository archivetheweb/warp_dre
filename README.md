# Warp DRE

Rust package to interact with [Warp's](https://warp.cc/) DRE nodes.

Example

```rust
    let client = warp_dre::WarpDRE::new(WarpDREOptionsBuilder::default().build()?);
    let contract_tx_id = "_z0ch80z_daDUFqC9jHjfOL8nekJcok4ZRkE_UesYsk";

    let mut query: HashMap<String, String> = HashMap::new();
    query.insert("query".into(), "$.name".into());

    let res = client.get_contract_with_query(contract_tx_id, query).await?;
    let r = res.result.unwrap();
    let result = r[0].as_str();
    assert!(result == Some("VouchDAO"));
```
