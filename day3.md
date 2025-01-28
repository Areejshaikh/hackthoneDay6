Day 3
API Integration and Schema Migration Documentation

Overview
This documentation outlines the process for integrating the API and performing schema migrations.



 API Integration Process
1. **Sanity Client Setup:**
   - Imported the Sanity client.
   - Configured with `projectId`, `dataset`, `apiVersion`, and `token`.

2. **Fetching Products:**
   - Utilized a REST API to fetch product data.
   - Endpoint: `https://template1-neon-nu.vercel.app/api/products`.

3. **Uploading Images:**
   - Fetched images from external URLs.
   - Uploaded images to Sanity using the `assets.upload` method.

4. **Creating Documents:**
   - Constructed product documents with fields such as `name`, `price`, `image`, `slug`, etc.
   - Uploaded documents to Sanity using the `client.create` method.

---

 Schema Adjustments
 Modified Schema
- **Added Fields:**
  - `slug`: Automatically generates slugs from product names.
  - `rating`: Stores product ratings.
  - `quantity`: Tracks product stock.

- **Updated Field Types:**
  - Adjusted `category` to use predefined options.

 Example Schema File
import { defineType } from 'sanity';

export default defineType({
  name: 'products',
  title: 'Products',
  type: 'document',
  fields: [
    { name: 'name', title: 'Name', type: 'string' },
    { name: 'rating', title: 'Rating', type: 'number' },
    { name: 'price', title: 'Price', type: 'number' },
    { name: 'slug', title: 'Slug', type: 'slug', options: { source: 'name' } },
    { name: 'category', title: 'Category', type: 'string', options: { list: [
      { title: 'T-Shirt', value: 'tshirt' },
      { title: 'Jeans', value: 'jeans' },
    ] } },
  ],
});
```

---

 Migration Steps
1. **Export Data:**
   - Backed up existing data using Sanity's export tool.

2. **Schema Update:**
   - Applied changes to the schema in the `products` file.

3. **Migration Tool:**
   - Used the Sanity CLI to deploy schema updates:
     sanity deploy
     sanity dataset import
     ```

4. **Data Re-import:**
   - Re-imported updated data using Sanity’s import tool to align with the new schema.

---

## Tools and Commands Used
- **Sanity CLI:** For deploying and migrating.
- **Fetch API:** For external data integration.
- **Node.js:** For scripting the upload process.

### Example Commands
`# API Integration and Schema Migration Documentation

## Overview
This documentation outlines the process for integrating the API and performing schema migrations.

---

## API Integration Process
1. **Sanity Client Setup:**
   - Imported the Sanity client.
   - Configured with `projectId`, `dataset`, `apiVersion`, and `token`.

2. **Fetching Products:**
   - Utilized a REST API to fetch product data.
   - Endpoint: `https://template1-neon-nu.vercel.app/api/products`.

3. **Uploading Images:**
   - Fetched images from external URLs.
   - Uploaded images to Sanity using the `assets.upload` method.

4. **Creating Documents:**
   - Constructed product documents with fields such as `name`, `price`, `image`, `slug`, etc.
   - Uploaded documents to Sanity using the `client.create` method.

---

## Schema Adjustments
### Modified Schema
- **Added Fields:**
  - `slug`: Automatically generates slugs from product names.
  - `rating`: Stores product ratings.
  - `quantity`: Tracks product stock.

- **Updated Field Types:**
  - Adjusted `category` to use predefined options.

### Example Schema File
```javascript
import { defineType } from 'sanity';

export default defineType({
  name: 'products',
  title: 'Products',
  type: 'document',
  fields: [
    { name: 'name', title: 'Name', type: 'string' },
    { name: 'rating', title: 'Rating', type: 'number' },
    { name: 'price', title: 'Price', type: 'number' },
    { name: 'slug', title: 'Slug', type: 'slug', options: { source: 'name' } },
    { name: 'category', title: 'Category', type: 'string', options: { list: [
      { title: 'T-Shirt', value: 'tshirt' },
      { title: 'Jeans', value: 'jeans' },
    ] } },
  ],
});
```

---

## Migration Steps
1. **Export Data:**
   - Backed up existing data using Sanity's export tool.

2. **Schema Update:**
   - Applied changes to the schema in the `products` file.

3. **Migration Tool:**
   - Used the Sanity CLI to deploy schema updates:
     ```bash
     sanity deploy
     sanity dataset import
     ```

4. **Data Re-import:**
   - Re-imported updated data using Sanity’s import tool to align with the new schema.

---

## Tools and Commands Used
- **Sanity CLI:** For deploying and migrating.
- **Fetch API:** For external data integration.
- **Node.js:** For scripting the upload process.

### Example Commands
```bash
sanity init
sanity dataset export production export.tar.gz
sanity dataset import export.tar.gz
```

---

## Notes
- Ensure tokens and sensitive credentials are stored securely.
- Test migrations in a staging environment before production deployment.

sanity init
sanity dataset export production export.tar.gz
sanity dataset import export.tar.gz
```

---

## Notes
- Ensure tokens and sensitive credentials are stored securely.
- Test migrations in a staging environment before production deployment.



file:///C:/Users/Online%20Laptop/Downloads/merged%20(2).pdf