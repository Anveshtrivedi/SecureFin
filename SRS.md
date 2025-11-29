# Software Requirements Specification (SRS)
**Project Name:** SecureFin
**Version:** 1.0
**Status:** Draft

---

## 1. Introduction

### 1.1 Purpose
The purpose of this document is to define the software requirements for **SecureFin**, a comprehensive fintech platform designed to enhance financial literacy, provide AI-driven financial planning, and facilitate secure blockchain-based transactions. This document covers the functional and non-functional requirements, system architecture, and external interfaces.

### 1.2 Scope
SecureFin is a web-based application that integrates:
*   **Financial Education:** A dedicated module for scam awareness and financial literacy using videos and quizzes.
*   **AI Financial Planning:** "OptiBudget," a tool that uses Google Gemini AI to generate personalized budget plans and investment strategies.
*   **Blockchain Wallet:** "SecureFin," a crypto wallet interface for managing SFT (Secure Financial Token) on the Polygon Amoy Testnet.
*   **Dashboard:** A centralized hub for tracking expenses, budgets, and system status.

### 1.3 Definitions, Acronyms, and Abbreviations
*   **SFT:** Secure Financial Token (Custom ERC-20 Token).
*   **AI:** Artificial Intelligence (specifically Google Gemini).
*   **UI/UX:** User Interface / User Experience.
*   **RBAC:** Role-Based Access Control.
*   **Polygon Amoy:** The blockchain testnet used for transactions.

---

## 2. Overall Description

### 2.1 Product Perspective
SecureFin operates as a standalone web application but relies on external services:
*   **Google Gemini API** for AI logic.
*   **Polygon Blockchain** for token transactions.
*   **NeonDB (PostgreSQL)** for structured data storage.
*   **MetaMask** for user wallet authentication and transaction signing.

### 2.2 User Classes and Characteristics
*   **General User:** Individuals seeking financial literacy, budgeting tools, and a secure way to transfer tokens.
*   **Administrator:** System managers responsible for overseeing user activity and system health (via the Admin Dashboard).

### 2.3 Operating Environment
*   **Client:** Modern web browsers (Chrome, Firefox, Edge, Safari).
*   **Server:** Node.js environment (Next.js SSR).
*   **Database:** Cloud-hosted PostgreSQL (NeonDB).
*   **Blockchain:** EVM-compatible network (Polygon Amoy).

---

## 3. System Features (Functional Requirements)

### 3.1 Module 1: Vitta Raksha (Financial Literacy)
*   **FR-1.1:** The system shall display a curated list of educational videos regarding financial scams.
*   **FR-1.2:** The system shall provide AI-generated summaries for each video using the Gemini API.
*   **FR-1.3:** The system shall offer interactive quizzes to test user knowledge, with immediate feedback on answers.
*   **FR-1.4:** The system shall present real-world case studies with "Risks" and "Protection" breakdowns.

### 3.2 Module 2: OptiBudget (AI Planner)
*   **FR-2.1:** Users shall be able to input monthly income, financial goals, and risk tolerance.
*   **FR-2.2:** The system shall generate a 50/30/20 budget breakdown using AI.
*   **FR-2.3:** The system shall suggest investment strategies (Asset Allocation) based on user capital and risk profile.
*   **FR-2.4:** The system shall analyze expense inputs to provide actionable money-saving tips.

### 3.3 Module 3: SecureFin Wallet
*   **FR-3.1:** Users shall be able to connect their MetaMask wallet.
*   **FR-3.2:** The system shall display the user's current SFT and MATIC balances.
*   **FR-3.3:** Users shall be able to transfer SFT tokens to other addresses.
*   **FR-3.4:** The system shall display a history of recent transactions fetched from the blockchain.

### 3.4 Module 4: Dashboard
*   **FR-4.1:** The system shall visualize expense data using Bar and Radar charts.
*   **FR-4.2:** The system shall track budget constraints (Monthly Limit vs. Spent) using progress bars.
*   **FR-4.3:** The system shall provide an Admin view for monitoring system stats (Total Users, Active Sessions).

---

## 4. External Interface Requirements

### 4.1 User Interfaces
*   **Design Style:** Dark mode, glassmorphism effects, and responsive layout (Mobile/Desktop).
*   **Navigation:** Persistent top navigation bar with links to all modules and a dynamic "Back" button for sub-pages.

### 4.2 Software Interfaces
*   **Database:** PostgreSQL connection via `pg` pool with SSL encryption.
*   **AI Service:** REST API calls to Google Gemini (`gemini-2.5-flash`).
*   **Blockchain:** JSON-RPC connection via Ethers.js to Polygon Amoy.

---

## 5. Non-Functional Requirements

### 5.1 Performance
*   **Response Time:** AI responses should load within 3-5 seconds.
*   **Blockchain Latency:** Transaction confirmation depends on network congestion but UI must provide "Pending" states.

### 5.2 Safety & Security
*   **Data Privacy:** No sensitive banking passwords are stored; wallet keys remain in MetaMask.
*   **Connection Security:** All database and API connections must use TLS/SSL.
*   **Smart Contract:** The SFT contract must follow standard ERC-20 security practices.

### 5.3 Reliability
*   **Availability:** The web application should be available 99.9% of the time.
*   **Error Handling:** The system must gracefully handle API failures (e.g., AI timeout, Blockchain RPC error) and inform the user.

---

## 6. Appendix
*   **Tech Stack:** Next.js, TypeScript, Tailwind CSS, Ethers.js, PostgreSQL.
*   **Future Scope:** Integration with real banking APIs (Account Aggregators), mobile app development, and multi-chain support.
