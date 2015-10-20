aws-s3-bucket-listing
=====================

List files in a S3 bucket in a web browser with a link to each file (cf. [example](http://regexp.s3.amazonaws.com/list.html)).

INSTALLATION & BUCKET CONFIGURATION
-----------------------------------

Upload the file [list.html](https://raw.githubusercontent.com/caussourd/aws-s3-bucket-listing/master/list.html) in your bucket

### In the bucket Permissions
- Grant Everyone to list
- Add this bucket policy, replacing \<your_bucket_name>\:
```
{
    "Version": "2008-10-17",
    "Statement": [
		    {
			"Sid": "PublicReadGetObject",
			"Effect": "Allow",
			"Principal": {
				"AWS": "*"
			},
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::<your_bucket_name>/*"
		}
	]
}
 ```

**Note:** It's not necessary to activate the website hosting

### Access the web page
Display the list at this address: 
**http://\<your_bucket_name\>.\<your_endpoint\>/list.html**

To know what is your endpoint: http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region. Example for Europe (Ireland): `http://bucketname.s3-eu-west-1.amazonaws.com/list.html`

**Note**: It also works with HTTPS. It won't work with a S3 website endpoint (the hostname must point to the request endpoint)

RANDOM INFORMATION
------------------
- It is compatible with Internet Explorer (has been tested with IE7, IE8 and IE9)
- It doesn't follow folders 

SOURCE
------
http://aws.amazon.com/code/Amazon-S3/1713

Only this documentation has been added

EXAMPLE
-------
http://regexp.s3.amazonaws.com/list.html
