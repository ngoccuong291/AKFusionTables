AKFusionTables
==============

Google Fusion Table library on iOS to support the api version 1.0


I took the old libray from Pavel Aksonov. Improved it to support the new version api of google fusion because the old google fusion table is deprecated.

Just download the source code, include them into your project and you are good to go

Example:

<pre><code>
AKFusionTables *fusionTables = [[AKFusionTables alloc] initWithUsername:kGoogleUser password:kGooglePass apiKey:kApiKey];
    
NSString *sql = [NSString stringWithFormat:@"INSERT INTO %@ (Text,Number,Date) VALUES('TEST2', 321, '1/1/2013')"
        , kTableId];
[fusionTables modifySql:sql completionHandler:^(NSData *data, NSError *completeError) {
    if (completeError != nil){
        NSInteger code = [completeError code];
        NSLog(@"Error code %d", code);
    } else {
        NSString *content = [[NSString alloc]
                initWithBytes:[data bytes] length:[data length] encoding:NSUTF8StringEncoding];
        NSLog(@"Content: %@", content);
        [content release];

    }
}];
[fusionTables release];
</code></pre>

* https://developers.google.com/fusiontables/docs/v1/getting_started
* https://developers.google.com/fusiontables/docs/v1/using
* https://developers.google.com/fusiontables/docs/v1/migration_guide
* To get the API-Key: https://developers.google.com/fusiontables/docs/v1/using#APIKey