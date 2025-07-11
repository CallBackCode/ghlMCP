# GoHighLevel MCP Server

A robust Model Context Protocol (MCP) server for the GoHighLevel API, providing tools for managing contacts.

## Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/CallBackCode/ghlMCP.git
   cd ghlMCP
   ```
2. **Install dependencies:**
   ```sh
   npm install
   ```
3. **Set your GoHighLevel API key and location ID:**

   - Create a `.env` file in the project root:

     ```sh
     cat <<EOF > .env
     # --- Required: Agency Token or Location Token and Location ID ---
     GHL_API_KEY=your_api_key_here
     GHL_LOCATION_ID=your_location_id_here

     # --- Optional: Test Only Variables ---

     GHL_TEST_BUSINESS_ID=your_business_id_here
     GHL_TEST_CONTACT_ID=your_contact_id_here

     EOF
     ```

````

4. **Build the project:**

   ```sh
   npm run build
````

5. **Run the MCP server:**

   ```sh
   npm start
   ```

6. **Run tests:**
   ```sh
   npm test
   ```

## Environment Variables

- `GHL_API_KEY` (required): Your GoHighLevel API key
- `GHL_LOCATION_ID` (required): Your GoHighLevel location ID

**Optional: Test Only**

- `GHL_TEST_BUSINESS_ID`: Used for businessId-based contact tests
- `GHL_TEST_CONTACT_ID`: Used for contactId-based tests (if needed)

## Available MCP Endpoints (Tools)

<details>
<summary><strong>Contacts</strong></summary>

| Endpoint                  | Description                      | Required Params            | Optional Params                           |
| ------------------------- | -------------------------------- | -------------------------- | ----------------------------------------- |
| `listContacts`            | List all contacts                | `locationId`               |                                           |
| `getContact`              | Get a contact by ID              | `id`, `locationId`         |                                           |
| `createContact`           | Create a new contact             | `locationId`               | `firstName`, `lastName`, `email`, `phone` |
| `updateContact`           | Update a contact by ID           | `id`, `locationId`         | `firstName`, `lastName`, `email`, `phone` |
| `deleteContact`           | Delete a contact by ID           | `id`, `locationId`         |                                           |
| `upsertContact`           | Upsert (create/update) a contact | `locationId`, `email`      | `firstName`, `lastName`, `phone`          |
| `getContactsByBusinessId` | Get contacts by businessId       | `businessId`, `locationId` | `limit`, `skip`, `query`                  |

</details>

<!--
Add more <details> blocks for other edges (e.g., organizations, tasks) if/when implemented.
-->

## Project Structure

- `src/api/` — API wrappers for GoHighLevel endpoints
- `src/types/` — Centralized TypeScript types
- `src/index.ts` — MCP server entry point
- `test/` — Jest test suites for each endpoint

## Notes

- All endpoints require a valid GoHighLevel API key and location ID.
- Responses are returned as pretty-printed JSON in text format for LLM compatibility.
- See [GoHighLevel API Docs](https://github.com/GoHighLevel/highlevel-api-docs) for more details.

---

Provided by CallBack
