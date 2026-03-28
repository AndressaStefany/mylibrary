# Requirements Document - Personal Library Manager

## 1. Project Overview
A full-stack web application designed to catalog and manage a personal collection of physical and digital books. The system aims to automate data entry via barcode scanning (ISBN) and provide insights into reading habits through data visualization and future AI integration.

## 2. Milestone 1: Book Capture (The MVP)
The primary goal of this phase is to build the core infrastructure to register books with minimal manual effort.

### 2.1. Functional Requirements (RF)
- **[RF-01] Barcode Scanning**: The system must use the device's camera to scan ISBN barcodes from physical books.
- **[RF-02] External Metadata Fetch**: Upon scanning an ISBN, the system must fetch book details (Title, Author, Genre, Page Count, Synopsis, Cover URL) from external APIs (Google Books/Open Library).
- **[RF-03] Manual Confirmation Form**: Users must be able to review and edit fetched data before saving.
- **[RF-04] Reading Status**: Users must assign a status to each book: To Read, Reading, Read, Re-reading, Abandoned.
- **[RF-05] Personal Metadata**: Users can manually add information not always present in APIs, such as:
  - Language (Portuguese, English, French).
  - Country of Origin.
  - Personal Rating (1-5 stars) for finished books.
- **[RF-06] Manual Cover Upload**: If the API doesn't provide a cover, the user must be able to upload an image.

### 2.2. Non-Functional Requirements (RNF)
- **[RNF-01] Responsiveness**: The interface must be mobile-friendly, as scanning will primarily happen via smartphone.
- **[RNF-02] Database**: Use PostgreSQL for relational data integrity and future complex analytical queries.
- **[RNF-03] Infrastructure**: The database must run inside a Docker container for environment consistency.
- **[RNF-04] Performance**: Barcode detection should happen in real-time with low latency.

## 3. Data Model (Conceptual)

| Entity | Key Attributes |
|--------|----------------|
| Book   | ISBN, Title, Synopsis, Page Count, Status, Rating, Language, Country, Cover URL |
| Author | Name, Nationality (optional) |
| Genre  | Name (e.g., Sci-Fi, Biography, Philosophy) |

## 4. Technical Stack

To ensure scalability and future integration with Machine Learning models, the following technologies have been selected:
- Frontend: React with TypeScript (for type safety and component-based UI).
- Backend: Python using FastAPI (high-performance asynchronous framework with automatic OpenAPI documentation).
- Database: PostgreSQL (relational database for robust data integrity and complex analytical queries).
- Infrastructure: Docker & Docker Compose (for containerized environment and easy deployment).
- ORM: SQLModel (combines SQLAlchemy and Pydantic for seamless integration with FastAPI and type validation).

## 5. Future Scope (Release 2 & Beyond)
- **Dashboard & Stats**: Visualization of most read genres, pages per month, and distribution by country/language.
- **AI Reading Assistant**: A chatbot integrated with the database to suggest the next read based on user history and preferences.
- **E-book Integration**: Support for uploading/parsing metadata from .epub or .pdf files.