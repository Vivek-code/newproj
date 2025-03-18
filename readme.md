# **Content Recommendation Microservice**

A scalable and personalized content recommendation microservice built with **Python**, **FastAPI**, and **GenAI technologies**. It employs an **embedding-based recommendation algorithm** leveraging **Facebook BART Large MNLI** for content categorization and Kafka for asynchronous messaging.

---

## **Table of Contents**

1. [Overview](#overview)
2. [Features](#features)
3. [Architecture](#architecture)
4. [Technologies Used](#technologies-used)
5. [API Endpoints](#api-endpoints)
6. [Database Schema](#database-schema)
7. [Installation](#installation)
8. [Usage](#usage)
9. [Deployment](#deployment)
10. [Future Improvements](#future-improvements)

---

## **Overview**

This microservice provides personalized content recommendations to users based on their interests. It leverages:

- **GenAI** models for embedding-based recommendations.
- Scalable and conflict-free service architecture with clear separation of concerns.
- Kafka for asynchronous event handling.

### **Key Components**

1. **UserService**: Manages user embeddings, interactions, and real-time recommendations.
2. **FeedbackService**: Logs user feedback and balances user interests.
3. **ContentIngestService**: Processes and stores new content and metadata.

---

## **Features**

- Personalized recommendations based on user interests.
- Embedding-based categorization and retrieval using **Facebook BART Large MNLI**.
- Asynchronous updates via **Kafka**.
- Optimized for scalability, maintainability, and conflict-free operations.
- Supports real-time feedback to refine recommendations.

---

## **Architecture**

![Architecture Diagram Placeholder](#) _(Include or reference a diagram if available)_

### **Workflow Highlights**

- **UserService** exclusively manages embeddings with **Qdrant**.
- **Redis** caches category embeddings for fast user embedding computation.
- **MongoDB** stores user preferences and content metadata.
- Smart embedding updates triggered by **ContentIngestService**.

---

## **Technologies Used**

- **Python** & **FastAPI**: Backend development.
- **Facebook BART Large MNLI**: GenAI model for content categorization.
- **Kafka**: Event-driven architecture.
- **Qdrant**: Embedding storage and retrieval.
- **Redis**: In-memory caching for category embeddings.
- **MongoDB**: Storage for user preferences and content metadata.

---

## **API Endpoints**

### 1. **User Interest Submission**

**POST** `/api/user/interests`  
_Submits user interests and updates their embeddings._

### 2. **Content Recommendation Retrieval**

**GET** `/api/recommendations`  
_Returns personalized content recommendations._

### 3. **Feedback Collection**

**POST** `/api/user/feedback`  
_Logs feedback and adjusts user interests._

---

## **Database Schema**

### **Collections and Tables**

1. **User Interests**
   - UserID, Preferences, Embeddings, Interaction History
2. **Content Metadata**
   - ContentID, Title, Description, Category, Embeddings
3. **Feedback Logs**
   - UserID, FeedbackType, ContentID, Timestamp

### **Indexes**

- Use **FAISS** or **Annoy** for faster vector similarity searches on embeddings.

---

## **Installation**

### **Prerequisites**

- Python 3.12+
- Docker (optional, for containerized deployment)

### **Steps**

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-url.git
   cd content-recommendation-microservice
   ```
