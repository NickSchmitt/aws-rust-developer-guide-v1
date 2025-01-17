--------

 *This is documentation for the developer preview release of the AWS SDK for Rust\. Do not use it in production as it is subject to breaking changes\.* 

--------

# List identity pools<a name="cognito-sync_ListIdentityPoolUsage_rust_topic"></a>

The following code example shows how to list Amazon Cognito identity pools\.

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
async fn show_pools(client: &Client) -> Result<(), Error> {
    let response = client
        .list_identity_pool_usage()
        .max_results(10)
        .send()
        .await?;

    if let Some(pools) = response.identity_pool_usages() {
        println!("Identity pools:");

        for pool in pools {
            println!(
                "  Identity pool ID:    {}",
                pool.identity_pool_id().unwrap_or_default()
            );
            println!(
                "  Data storage:        {}",
                pool.data_storage().unwrap_or_default()
            );
            println!(
                "  Sync sessions count: {}",
                pool.sync_sessions_count().unwrap_or_default()
            );
            println!(
                "  Last modified:       {}",
                pool.last_modified_date().unwrap().to_chrono_utc()
            );
            println!();
        }
    }

    println!("Next token: {}", response.next_token().unwrap_or_default());

    Ok(())
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/cognitosync#code-examples)\. 
+  For API details, see [ListIdentityPoolUsage](https://awslabs.github.io/aws-sdk-rust/) in *AWS SDK for Rust API reference*\. 