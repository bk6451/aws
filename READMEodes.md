# aws

ses nodejs
var aws = require("aws-sdk");
var ses = new aws.SES({ region: "us-east-1" });
exports.handler = async function (event) {
  var params = {
    Destination: {
      ToAddresses: ["gayathrm@srmist.edu.in"],
    },
    Message: {
      Body: {
        Text: { Data: "Test" },
      },

      Subject: { Data: "Test Email" },
    },
    Source: "helenvia@srmist.edu.in",
  };
![Uploading image.png…]()


s3 optimization
import boto3
import json

s3 = boto3.resource('s3')

def lambda_handler (event, context):
 bucket = s3.Bucket('test-ndgegy4364gdu-source-bucket')
 dest_bucket=s3.Bucket('test-ndgegy4364gdu-destination-bucket')

 print(dest_bucket)
 print(bucket)
 
 for obj in bucket.objects.filter(Prefix='images/',Delimiter='/'):
  dest_key=obj.key
  print(dest_key)
  print('copy file ' + dest_key)
  s3.Object(dest_bucket.name, dest_key).copy_from(CopySource= {'Bucket': obj.bucket_name, 'Key': obj.key})
  print('delete file from source bucket ' + dest_key)
  s3.Object(bucket.name, obj.key).delete()
