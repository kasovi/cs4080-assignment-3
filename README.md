# DEMO VIDEO: https://youtu.be/3d7TFXB3y1E

## Overview

This project implements a multi-assistant framework that handles different types of user requests with specialized AI assistants.

- **MusicAssistant**: Recommends songs based on mood and preferences. Premium users get a longer list of AI generated songs.
- **FitnessAssistant**: Suggests workouts based on fitness goals and experience level. Premium users get meal plans.
- **StudyAssistant**: Explains a set of AI-related academic topics
- **GeneralAssistant**: Handles general queries and has fallback responses

## How to Run

In directory containing python file:
python main.py

The program asks whether the user would rather run a premade demo with hardcoded users and questions, or an interactive session where they can ask questions. Premade demo also includes additional details about requests and responses like timestamp, detected type, and confidence.

## Architecture & Implementation

### Part 1: Data Type Design
- **UserProfile**: Custom data type with name, age, preferences dict, and premium status
- **Request**: Input string, timestamp, and command type enumeration
- **Response**: Message and action performed flag
- **CommandType**: Enumeration for MUSIC, FITNESS, STUDY, and GENERAL commands

All classes have validation and error handling

### Part 2: Core OOP Structure
- **AIAssistant**: Base class with greetUser(), handleRequest(), and generateResponse() methods
- **Inheritance**: All specialized assistants inherit from AIAssistant
- **Polymorphism**: Each subclass overrides handleRequest() with unique behavior and adds additional behavior with functions like explainTopic
- **Encapsulation**: Private data structures for music database, workout plans, and study bot knowledge base

### Part 3: Dynamic Behavior & User Simulation
- **AssistantManager**: Routes requests to appropriate assistant based on command type
- **CommandParser**: Extracts keywords and preferences from user input
- **User simulation**: Can initialize different users with varying preferences, also allows user to enter their name and age
- **Keyword-based intent classification**: Automatically detects music, fitness, study, or general requests

## Other Main Features

- **Smart keyword extraction**: Detects mood (such as "happy", "energetic"), fitness level ("beginner", "advanced"), and topics ("oop", "python") from natural language by searching through lists of keywords for matches
- **Premium users**: Aditional responses for premium users in the music and fitness bots, providing extended AI generated music and meal plans using the openAI chatgpt 4.0 API.
- **Confidence scoring**: Each response includes a confidence level, although this doesn't have any technical meaning in this version since the model is mainly conceptual.
- **Fallback handling**: Handles unrecognized commands by reverting to more generic query prompts


## OOP Concepts

- **Encapsulation**: Separates attributes and methods among different class types
- **Inheritance**: Specialized assistants extend base AIAssistant
- **Polymorphism**: Different handleRequest() implementations for each assistant type
