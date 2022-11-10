### YAML101
- Human readable data serialization language
- Unordered collection of key:value pairs
	- key: value - cat1: winkie
- YAML supports numbers (1 or 2 ...), floats (1.337), bools (true or failse), and null
- Lists
	- Ordered set of values
		- `adrianscats: ["roffle", "truffles", "penny", "winkie"]`
		- ![[Pasted image 20221029112024.png | 800]]
- Dictionary
	- Ordered set of key:value pairs
	- ![[Pasted image 20221029112247.png | 500]]
	- Using YAML key:value pairs, lists, and dicts, allows you to build complex data structures in a wat which is human readable
	- Cloudformation YAML template example
```yaml
Resources: #dictionary
  s3bucket: #dictionary
    Type: "AWS::S3::Bucket" #key
    Properties: #key 
      BucketName: "ac1337catpics" #value
```

### JSON101
- JavaScript Object Notation - Lightweight data-interchange format
- Object - unordered set of key:value pairs enclosed by { } - dictionary
- Array - ordered collection of values separated by commas and enclosed in [  ] - list
- Values = string, object, number, array, true, false, null
- {} at the top tells that what's enclosed is a json object
```json
{
  "cats": ["roffle", "truffles", "penny", "winkie"],
  "colors": ["mixed", "mixed", "grey", "white"],
  "numofeyes": ["2", "2", "2", "1"]
}
```

- ![[Pasted image 20221029114301.png | 800]]

```json
{
  "Resources": {
  "s3bucket": {
     "Type": "AWS::S3::Bucket",
     "Properties": {
       "BucketName": "ac1337catpics"
     }
   }
 }
}
```

### Encryption 101
- Encryption approaches
	- Encryption at rest
		- designed to protect against a physical threat
	- Encryption in transit
		- designed to protect data while it's being transferred
- Encryption concepts
	- Plaintext - unencrypted data
	- Algorithm - code and math that encrypts data
		- Blowfish, AES, RC4, DES, RC5, RC6
	- Key - Password
	- Ciphertext - encrypted data
	- ![[Pasted image 20221029115156.png | 300]]
- Symmetric Encryption