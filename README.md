# Vinted API Documentation
This API retrieves product information, reviews, search, seller information and a whole lot more from Vinted. This API is listed on [RapidAPI](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/vinted-api3)

Link: [https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/vinted-api3](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/vinted-api3)

Base URL: `https://vinted-api3.p.rapidapi.com/`

## Authentication

All requests must include the following headers:
- `X-RapidAPI-Key`: Your RapidAPI key
- `X-RapidAPI-Host`: vinted-api3.p.rapidapi.com

## Common Parameters

Most endpoints accept a `country` parameter:
- Default value: 'us'
- Must be a valid country code supported by Vinted domains
- Case-insensitive

## Endpoints

### 1. Search Products
```
GET /search
```

Search for products across the Vinted platform.

**Parameters:**
- `query` (required): Search term
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 96)
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /search?query=nike&page=1&perPage=96&country=us
```

### 2. Similar Products
```
GET /similar
```

Find products similar to a specific item.

**Parameters:**
- `productId` (required): ID of the reference product
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /similar?productId=12345&country=us
```

### 3. Product Description
```
GET /description
```

Get detailed description of a specific product.

**Parameters:**
- `productId` (required): ID of the product
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /description?productId=12345&country=us
```

### 4. Seller Information
```
GET /seller-info
```

Retrieve detailed information about a seller.

**Parameters:**
- `sellerId` (required): ID of the seller
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /seller-info?sellerId=12345&country=us
```

### 5. Seller Products
```
GET /seller-products
```

Get all products listed by a specific seller.

**Parameters:**
- `sellerId` (required): ID of the seller
- `country` (optional): Country code (default: 'us')
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 20)

**Example Request:**
```
GET /seller-products?sellerId=12345&page=1&perPage=20&country=us
```

### 6. Seller Items Facets
```
GET /seller-itemsfacet
```

Get aggregated information about a seller's items.

**Parameters:**
- `sellerId` (required): ID of the seller
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /seller-itemsfacet?sellerId=12345&country=us
```

### 7. Seller Feedback
```
GET /seller-feedback
```

Retrieve feedback left for a seller.

**Parameters:**
- `sellerId` (required): ID of the seller
- `country` (optional): Country code (default: 'us')
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 20)

**Example Request:**
```
GET /seller-feedback?sellerId=12345&page=1&perPage=20&country=us
```

### 8. Seller Feedback Summary
```
GET /seller-feedback-summary
```

Get aggregated feedback statistics for a seller.

**Parameters:**
- `sellerId` (required): ID of the seller
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /seller-feedback-summary?sellerId=12345&country=us
```

### 9. Search by Catalog
```
GET /searchby-catalog
```

Search products within a specific catalog category.

**Parameters:**
- `catalogId` (optional): Category ID (default: '2050')
- `query` (optional): Search term (default: '')
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 96)
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /searchby-catalog?catalogId=2050&query=shoes&page=1&perPage=96&country=us
```

### 10. Full Search
```
GET /search-full
```

Advanced search with multiple filters.

**Parameters:**
- `query` (required): Search term
- `catalogId` (optional): Category ID
- `size_ids` (optional): Comma-separated size IDs
- `brand_ids` (optional): Comma-separated brand IDs
- `status_ids` (optional): Comma-separated status IDs
- `color_ids` (optional): Comma-separated color IDs
- `material_ids` (optional): Comma-separated material IDs
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 96)
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /search-full?query=dress&brand_ids=53,54&color_ids=1,2&page=1&country=us
```

### 11. Get Brands
```
GET /brands
```

Retrieve list of available brands.

**Parameters:**
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /brands?country=us
```

### 12. Search by Brand
```
GET /searchby-brand
```

Search products from specific brands.

**Parameters:**
- `brand_ids` (optional): Brand ID (default: '53')
- `query` (optional): Search term (default: '')
- `page` (optional): Page number (default: 1)
- `perPage` (optional): Items per page (default: 96)
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /searchby-brand?brand_ids=53&query=jacket&page=1&country=us
```

### 13. Feed Products
```
GET /feed-products
```

Get homepage/feed products.

**Parameters:**
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /feed-products?country=us
```

### 14. Get Colors
```
GET /colors
```

Retrieve available color options.

**Parameters:**
- `country` (optional): Country code (default: 'us')

**Example Request:**
```
GET /colors?country=us
```

## Error Handling

The API returns standard HTTP status codes:
- 200: Success
- 400: Bad Request (missing required parameters)
- 500: Server Error

Error responses include a message field explaining the error:
```json
{
    "message": "Please provide the required parameter"
}
```

## Caching

All endpoints implement caching to improve performance. Cached results are returned when the same request parameters are used within the cache validity period.

## Best Practices

1. Always check for required parameters before making requests
2. Use pagination parameters (`page` and `perPage`) to manage large result sets
3. Include error handling in your implementation
4. Use the country parameter appropriate for your target market
5. Cache results on your end when possible to minimize API calls

## Rate Limiting

Refer to your RapidAPI subscription plan for specific rate limiting details.


## Frequently Asked Questions (FAQs)

### General Questions

**Q: What is the Vinted API?**
A: The Vinted API is a RESTful interface that allows developers to programmatically access Vinted's marketplace data, including product listings, seller information, and search functionality. It's available through RapidAPI and provides comprehensive access to Vinted's platform features.

**Q: What can I build with the Vinted API?**
A: You can build various applications including:
- Price comparison tools
- Market analysis applications
- Shopping assistants
- Inventory management systems
- Social commerce platforms
- Fashion trend analysis tools
- Marketplace aggregators

**Q: Is the Vinted API official?**
A: This API is a third-party solution available through RapidAPI that interfaces with Vinted's platform. For official integrations, please contact Vinted directly.

### Technical Questions

**Q: How do I handle pagination in the API?**
A: Most endpoints support pagination through the `page` and `perPage` parameters. Example:
```javascript
// First page with 96 items
GET /search?query=nike&page=1&perPage=96

// Second page
GET /search?query=nike&page=2&perPage=96
```

**Q: What are the rate limits for the API?**
A: Rate limits depend on your RapidAPI subscription plan. Check your plan details on RapidAPI for specific limits.

**Q: How can I optimize my API usage?**
A: Several ways to optimize:
1. Implement client-side caching
2. Use appropriate page sizes
3. Filter results using available parameters
4. Handle rate limits properly
5. Implement error handling and retries

### Integration Questions

**Q: How do I get started with the API?**
A: Follow these steps:
1. Sign up for a RapidAPI account
2. Subscribe to the Vinted API
3. Get your API key
4. Make your first request using the provided documentation

**Q: What programming languages are supported?**
A: The API can be used with any programming language that supports HTTP requests. RapidAPI provides code examples in:
- Python
- JavaScript/Node.js
- PHP
- Ruby
- Java
- C#
- Go
- Swift

## Content Sections

### Understanding Vinted Marketplace Integration

The Vinted API provides developers with powerful tools to integrate second-hand fashion marketplace functionality into their applications. Whether you're building a sustainable fashion platform, market analysis tool, or price comparison service, this API offers comprehensive access to Vinted's extensive marketplace data.

### Key Features and Use Cases

1. **Product Search and Discovery**
   - Advanced search capabilities
   - Filter by brands, sizes, and colors
   - Similar product recommendations
   - Category-based browsing

2. **Seller Analytics**
   - Detailed seller profiles
   - Feedback analysis
   - Product portfolio insights
   - Performance metrics

3. **Market Research**
   - Price trend analysis
   - Brand popularity tracking
   - Category demand assessment
   - Regional market differences

4. **E-commerce Integration**
   - Product catalog integration
   - Real-time pricing data
   - Inventory management
   - Cross-platform synchronization

### Best Practices for Implementation

#### 1. Error Handling
```javascript
try {
    const response = await fetch('/search?query=nike');
    const data = await response.json();
} catch (error) {
    console.error('API Error:', error);
    // Implement retry logic or fallback
}
```

#### 2. Rate Limit Management
```javascript
class RateLimiter {
    constructor(maxRequests, timeWindow) {
        this.requests = [];
        this.maxRequests = maxRequests;
        this.timeWindow = timeWindow;
    }

    async throttle() {
        const now = Date.now();
        this.requests = this.requests.filter(time => now - time < this.timeWindow);
        
        if (this.requests.length >= this.maxRequests) {
            await new Promise(resolve => setTimeout(resolve, this.timeWindow));
