# Approver Management Service

## Overview

The Approver Management Service is a backend service for managing approvers within a Shopify application. This service provides various functions to create, find, update, and delete approvers in the database. It ensures that all operations are performed efficiently and handles any errors that may occur during these operations.

## Functions

1. [Create Approver](#create-approver)
2. [Create Many Approvers](#create-many-approvers)
3. [Find One Approver](#find-one-approver)
4. [Find Many Approvers](#find-many-approvers)
5. [Find Many Approvers By Customer](#find-many-approvers-by-customer)
6. [Update Approver](#update-approver)
7. [Delete Approver](#delete-approver)

## Dependencies

- **Logger**: Used for logging errors and other information.
- **Database Module**: Provides functions to interact with the database.

```javascript
const logger = require("../logger");
const {
  DB_TABLES,
  findManyDB,
  findOneDB,
  createDB,
  updateDB,
  deleteManyDB,
  transactionDB,
} = require("../db/index");
```

## Create Approver

Creates a new approver in the database.

```javascript
exports.createApproverService = async ({
  approverData,
  transactionPrismaEntity = null,
}) => {
  try {
    const createApprover = await createDB({
      createDBDto: approverData,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });

    return createApprover;
  } catch (error) {
    logger.error("Error creating approver: %o", error);
    throw error;
  }
};
```

### Use Case

Used when a new approver needs to be added to the system.

## Create Many Approvers

Creates multiple approvers in the database.

```javascript
exports.createManyApproversService = async ({
  approversData,
  transactionPrismaEntity = null,
}) => {
  try {
    const createManyApprovers = await createManyDB({
      createManyDBDto: approversData,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });

    return createManyApprovers;
  } catch (error) {
    logger.error("Error creating multiple approvers: %o", error);
    throw error;
  }
};
```

### Use Case

Used when multiple approvers need to be added to the system at once.

## Find One Approver

Finds one approver by filter options.

```javascript
exports.findOneApproverService = async ({
  filterOptions,
  selectOptions = {},
  transactionPrismaEntity = null,
}) => {
  try {
    const approver = await findOneDB({
      filterOptions,
      selectOptions,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });
    return approver;
  } catch (error) {
    logger.error("Error finding approver: %o", error);
    throw error;
  }
};
```

### Use Case

Used to find a specific approver based on certain criteria.

## Find Many Approvers

Finds many approvers with pagination, filtering, and sorting.

```javascript
exports.findManyApproversService = async ({
  skip,
  take,
  search,
  searchValues,
  additionalConfiguration = {},
  filterOptions = {},
  selectOptions = {},
  orderByOptions = [],
  transactionPrismaEntity = null,
}) => {
  try {
    const approvers = await findManyDB({
      skip,
      take,
      search,
      searchValues,
      additionalConfiguration,
      filterOptions,
      selectOptions,
      orderByOptions,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });
    return approvers;
  } catch (error) {
    logger.error("Error finding approvers: %o", error);
    throw error;
  }
};
```

### Use Case

Used to find multiple approvers based on various criteria, with support for pagination, filtering, and sorting.

## Find Many Approvers By Customer

Finds many approvers by customer ID with pagination, filtering, and sorting.

```javascript
exports.findManyApproversByCustomerService = async (
  customerId,
  {
    skip,
    take,
    search,
    additionalConfiguration = {},
    filterOptions = {},
    selectOptions = {},
    orderByOptions = [],
    transactionPrismaEntity = null,
  }
) => {
  try {
    filterOptions = {
      ...filterOptions,
      customers: {
        some: {
          store_customer_id: customerId,
        },
      },
    };

    const approvers = await findManyDB({
      skip,
      take,
      search,
      searchValues: search && [
        { value: "name", type: "string" },
        { value: "email", type: "string" },
      ],
      additionalConfiguration,
      filterOptions,
      selectOptions,
      orderByOptions,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });

    return approvers;
  } catch (error) {
    logger.error("Error finding approvers by customer: %o", error);
    throw error;
  }
};
```

### Use Case

Used to find approvers associated with a specific customer ID, supporting pagination, filtering, and sorting.

## Update Approver

Updates an approver by filter options.

```javascript
exports.updateApproverService = async ({
  filterOptions,
  updateData,
  transactionPrismaEntity = null,
}) => {
  try {
    const updateApprover = await updateDB({
      filterOptions,
      updateDBDto: updateData,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });

    return updateApprover;
  } catch (error) {
    logger.error("Error updating approver: %o", error);
    throw error;
  }
};
```

### Use Case

Used to update an existing approver's information based on specified criteria.

## Delete Approver

Deletes an approver by filter options.

```javascript
exports.deleteApproverService = async ({
  filterOptions,
  transactionPrismaEntity = null,
}) => {
  try {
    const deleteApprover = await deleteManyDB({
      filterOptions,
      type: DB_TABLES.APPROVER,
      transactionPrismaEntity,
    });

    return deleteApprover;
  } catch (error) {
    logger.error("Error deleting approver: %o", error);
    throw error;
  }
};
```

### Use Case

Used to delete an existing approver from the system based on specified criteria.

Powereb by Byteex
