# 🚀 AWS CloudFormation Template for Amazon Bedrock Knowledge Base with Pinecone Integration

## 📖 Read more
You can find detailed article on this template here

## 📌 Overview
This AWS CloudFormation template provisions an Amazon Bedrock knowledge base integrated with Pinecone for vector storage. It also creates an Amazon S3 bucket for knowledge base data, an IAM role with necessary permissions, and an AWS Secrets Manager secret to store the Pinecone API key.

## 📦 Resources Created
### 1. **🗄️ Amazon S3 Bucket**
   - Stores data for the Amazon Bedrock knowledge base.
   - Named dynamically based on the `KnowledgeBaseName` parameter.

### 2. **🔐 IAM Role for Amazon Bedrock**
   - Grants Amazon Bedrock permissions to:
     - Access the S3 bucket.
     - Retrieve the Pinecone API key from AWS Secrets Manager.
     - Invoke the Amazon Titan embedding model.

### 3. **🔑 AWS Secrets Manager Secret**
   - Stores the Pinecone API key securely.
   - Secret name is derived from the `KnowledgeBaseName` parameter.

### 4. **📚 Amazon Bedrock Knowledge Base**
   - Configured as a vector-based knowledge base.
   - Uses the specified embedding model for text embeddings.
   - Stores vector data in Pinecone.

### 5. **📥 Amazon Bedrock Data Source**
   - Configured to ingest data from the provisioned S3 bucket.

## ⚙️ Parameters
| Parameter Name        | Description                                        | Default Value |
|----------------------|------------------------------------------------|---------------|
| `EmbeddingModel`     | ARN of the embedding model to use. Defaults to Amazon Titan v2. | `arn:aws:bedrock:us-east-1::foundation-model/amazon.titan-embed-text-v2:0` |
| `KnowledgeBaseName`  | Name of the knowledge base.                      | `knowledge-base` |
| `PineconeConnectionString` | Pinecone connection string (API endpoint). | `https://xxx.xxx.xxx.pinecone.io` |
| `PineconeApiKey`     | Pinecone API Key for authentication. | `{"apiKey": "xxxx_xxxxx_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"}` |
| `TextField`          | Field name in Pinecone to store raw text data. | `text` |
| `MetadataField`      | Field name in Pinecone to store metadata. | `metadata` |

## 🚀 Usage Instructions
1. **📤 Deploy the CloudFormation Stack**
   - Navigate to the AWS CloudFormation console.
   - Create a new stack and upload this template.
   - Provide values for parameters if different from defaults.
   - Deploy the stack.

2. **✅ Verify Created Resources**
   - Check the S3 bucket for storage.
   - Ensure the IAM role is properly assigned to Amazon Bedrock.
   - Validate the knowledge base and its Pinecone integration.

## 🔒 Security Considerations
- The Pinecone API key is stored securely in AWS Secrets Manager.
- The IAM role follows the principle of least privilege, allowing only necessary actions.

## 🔮 Future Enhancements
- Add support for additional vector database options.
- Implement tighter access controls on the Pinecone API key.
- Automate data ingestion workflows.

---
This template enables seamless integration between Amazon Bedrock and Pinecone for a scalable, vector-based knowledge retrieval system.

