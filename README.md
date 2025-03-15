# Redis Practice Project

## Overview
This project demonstrates how to use Redis as a data store for a restaurant application. It covers various Redis features, including hashes, lists, sets, sorted sets, and more. The goal is to help students understand Redis data structures and how they can be used in a real-world application.

## Why Redis?
- **In-memory data store**: Redis provides fast read/write operations.
- **Great for caching**: Reduces load on databases and improves performance.
- **High performance**: Handles large amounts of data with low latency.

## Features Used in Redis
1. **Hashes** - Used for storing structured objects.
2. **Lists** - Stores ordered lists of items (e.g., reviews).
3. **Sets** - Stores unique unordered items (e.g., cuisines).
4. **Sorted Sets** - Stores items with associated scores (e.g., restaurant ratings).
5. **Strings** - Basic key-value storage.
6. **RedisJSON** - Stores JSON documents.
7. **RediSearch** - Enables fast search queries.
8. **Bloom Filters** - Used for probabilistic data structures.

## Project Structure

### Cuisines API
- **GET /cuisines** - Retrieves all cuisines.
- **GET /cuisines/:cuisineId** - Retrieves all restaurants for a specific cuisine.

### Restaurants API
- **GET /restaurants?search=name** - Search restaurants by name.
- **POST /restaurants** - Creates a new restaurant.
- **GET /restaurants/top-rated** - Retrieves a sorted list of restaurants by rating.
- **POST /restaurants/:restaurantId/reviews** - Adds a review to a restaurant.
- **GET /restaurants/:restaurantId/reviews** - Retrieves reviews of a restaurant.
- **DELETE /restaurants/:restaurantId/reviews/:reviewId** - Deletes a specific review.
- **GET /restaurants/:restaurantId/location** - Retrieves restaurant location information.
- **GET /restaurants/:restaurantId** - Retrieves restaurant details.

## Redis Data Structures Used

### 1. Hashes
- Stores structured data (e.g., restaurant details)
```redis
HSET restaurant:1 id 1 name "Better Food" rating 5
HGET restaurant:1 name  # Returns "Better Food"
```

### 2. Lists
- Stores a sequence of items (e.g., reviews)
```redis
LPUSH reviews:restaurant1 "Review1" "Review2"
LRANGE reviews:restaurant1 0 -1  # Returns all reviews
```

### 3. Sets
- Stores unique items (e.g., available cuisines)
```redis
SADD cuisines "Italian" "Mexican"
SISMEMBER cuisines "Italian"  # Returns 1 if exists
```

### 4. Sorted Sets
- Stores items with a score (e.g., restaurant ratings)
```redis
ZADD restaurants:by_rating 3.5 restaurant1 4 restaurant2
ZRANGE restaurants:by_rating 0 -1 WITHSCORES  # Returns sorted list
```

## Getting Started
### Prerequisites
- Node.js
- Redis server installed

