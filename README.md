# ESLint Setup for LWC

This guide will walk you through setting up ESLint for Lightning Web Components (LWC) in your project.

## Introduction

This repository provides a comprehensive guide to setting up ESLint for Lightning Web Components (LWC) in Salesforce projects. ESLint is a powerful tool that helps developers write clean, consistent, and error-free code. By following this guide, you will ensure that your LWC codebase adheres to best practices and is free from common mistakes.

## Features

- **Comprehensive ESLint Configuration:** Includes setup for ESLint, Babel, and relevant plugins for LWC.
- **Salesforce-Specific Rules:** Leverages Salesforce's ESLint configurations to enforce best practices specific to LWC.
- **HTML Reporting:** Generates detailed HTML reports for easy review of linting results.
- **Jest Support:** Configured to recognize Jest globals, facilitating seamless testing integration.

## Prerequisites

Ensure you have [Node.js](https://nodejs.org/) installed on your machine.

## Installation Steps

1. **Install ESLint and necessary plugins:**

    ```bash
    npm install eslint @babel/core @babel/eslint-parser @lwc/eslint-plugin-lwc --save-dev
    ```

2. **Install Salesforce and other ESLint configurations:**

    ```bash
    npm install --save-dev @salesforce/eslint-config-lwc @lwc/eslint-plugin-lwc @salesforce/eslint-plugin-lightning eslint-plugin-import eslint-plugin-jest
    ```

3. **Install HTML reporter for ESLint:**

    ```bash
    npm install eslint eslint-html-reporter --save-dev
    ```

## Configuration

Create an `.eslintrc` file in the root of your project with the following content:

```.eslintrc
{
    "extends": ["@salesforce/eslint-config-lwc/recommended", "@salesforce/eslint-config-lwc/ssr","@salesforce/eslint-config-lwc/i18n","eslint:recommended"],
    "parser": "@babel/eslint-parser",
    "parserOptions": {
        "requireConfigFile": false,
        "babelOptions": {
            "parserOpts": {
                "plugins": ["classProperties", ["decorators", { "decoratorsBeforeExport": false }],"typescript"]
            }
        }
    },

    "plugins": ["@lwc/eslint-plugin-lwc"],

    "rules": {
        "@lwc/lwc/no-deprecated": "error",
        "@lwc/lwc/valid-api": "error",
        "@lwc/lwc/no-document-query": "error",
        "@lwc/lwc/consistent-component-name": "error",
        "@lwc/lwc/no-api-reassignments": "error",
        "@lwc/lwc/no-async-await": "error",
        "@lwc/lwc/no-async-operation": "error",
        "@lwc/lwc/no-for-of": "error",
        "@lwc/lwc/no-inner-html": "error",
        "@lwc/lwc/no-leaky-event-listeners": "error",
        "@lwc/lwc/no-restricted-browser-globals-during-ssr": "error",
        "@lwc/lwc/no-unsupported-ssr-properties": "error",
        "@lwc/lwc/valid-graphql-wire-adapter-callback-parameters": "error",
        "array-callback-return": "error",
        "arrow-body-style": "error",
        "complexity": "error",
        "consistent-return": "error",
        "default-case": "error",
        "eqeqeq": "error",
        "grouped-accessor-pairs": "error",
        "handle-callback-err": "error",
        "max-params": "error",
        "no-console": "error",
        "no-dupe-class-members": "error",
        "no-else-return": "error",
        "no-empty": "error",
        "no-eq-null": "error",
        "no-mixed-spaces-and-tabs": "error",
        "no-new": "error",
        "no-param-reassign": "error",
        "no-restricted-globals": "error",
        "no-shadow": "error",
        "no-undef": "error",
        "no-unused-expressions": "error",
        "no-unused-vars": "error",
        "no-useless-return": "error",
        "radix": "error",
        "require-unicode-regexp": "error"
      }
}
