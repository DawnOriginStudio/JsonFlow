# JsonFlow Plugin for UE5

[Buy on fab.com](https://www.fab.com/zh-cn/listings/d7498b94-6243-482e-8c76-2036e2db4782)

JsonFlow is a comprehensive JSON serialization and deserialization plugin for Unreal Engine 5 Blueprint programming. It provides convenient Blueprint nodes for working with JSON data, supporting JSON Objects, JSON Arrays, and JSON Values with seamless conversion from various Blueprint basic types.

## Features

- **JSON Object Support**: Create, modify, and query JSON objects with Blueprint-friendly functions
- **JSON Array Support**: Handle JSON arrays with easy-to-use Blueprint nodes
- **JSON Value Support**: Work with individual JSON values of different types (string, number, boolean, null)
- **Blueprint Type Conversions**: Convert common UE5 types (Vector, Rotator, Transform, Color) to/from JSON
- **Parsing and Serialization**: Parse JSON strings and serialize JSON data back to strings
- **Type Safety**: Built-in type checking and validation for JSON operations

## Core Types

### FJsonFlowObject
Represents a JSON object that can contain key-value pairs.

### FJsonFlowArray
Represents a JSON array that can contain multiple JSON values.

### FJsonFlowValue
Represents a single JSON value that can be:
- String
- Number (float/integer)
- Boolean
- Null
- Object
- Array

### EJsonValueType
Enumeration for JSON value types:
- None
- Null
- String
- Number
- Boolean
- Array
- Object

## Blueprint Functions

### JSON Parsing
- **Parse Json String**: Parse a JSON string into a JsonFlowObject
- **Parse Json Array**: Parse a JSON array string into a JsonFlowArray

### JSON Serialization
- **Json Object To String**: Convert JsonFlowObject to JSON string (with optional pretty printing)
- **Json Array To String**: Convert JsonFlowArray to JSON string (with optional pretty printing)

### JsonFlowObject Operations
- **Create Json Object**: Create an empty JSON object
- **Has Field**: Check if a field exists in the JSON object
- **Get Field Names**: Get all field names from the JSON object
- **Remove Field**: Remove a field from the JSON object

#### Setting Values in JsonFlowObject
- **Set String Field**: Set a string value
- **Set Number Field**: Set a float value
- **Set Integer Field**: Set an integer value
- **Set Boolean Field**: Set a boolean value
- **Set Null Field**: Set a null value
- **Set Object Field**: Set a nested JSON object
- **Set Array Field**: Set a JSON array
- **Set Value Field**: Set a JsonFlowValue

#### Getting Values from JsonFlowObject
- **Get String Field**: Get a string value
- **Get Number Field**: Get a float value
- **Get Integer Field**: Get an integer value
- **Get Boolean Field**: Get a boolean value
- **Get Object Field**: Get a nested JSON object
- **Get Array Field**: Get a JSON array
- **Get Value Field**: Get a JsonFlowValue

### JsonFlowArray Operations
- **Create Json Array**: Create an empty JSON array
- **Get Array Length**: Get the number of elements in the array
- **Clear Array**: Remove all elements from the array

#### Adding Values to JsonFlowArray
- **Add String To Array**: Add a string value
- **Add Number To Array**: Add a float value
- **Add Integer To Array**: Add an integer value
- **Add Boolean To Array**: Add a boolean value
- **Add Null To Array**: Add a null value
- **Add Object To Array**: Add a JSON object
- **Add Array To Array**: Add a nested JSON array
- **Add Value To Array**: Add a JsonFlowValue

#### Getting Values from JsonFlowArray
- **Get String From Array**: Get a string value at index
- **Get Number From Array**: Get a float value at index
- **Get Integer From Array**: Get an integer value at index
- **Get Boolean From Array**: Get a boolean value at index
- **Get Object From Array**: Get a JSON object at index
- **Get Array From Array**: Get a nested JSON array at index
- **Get Value From Array**: Get a JsonFlowValue at index

### JsonFlowValue Operations
- **Make String Value**: Create a string JsonFlowValue
- **Make Number Value**: Create a float JsonFlowValue
- **Make Integer Value**: Create an integer JsonFlowValue
- **Make Boolean Value**: Create a boolean JsonFlowValue
- **Make Null Value**: Create a null JsonFlowValue
- **Get Value Type**: Get the type of a JsonFlowValue
- **Is Value Null**: Check if a JsonFlowValue is null

### Blueprint Type Conversions
- **Vector To Json Object**: Convert FVector to JSON object
- **Json Object To Vector**: Convert JSON object to FVector
- **Rotator To Json Object**: Convert FRotator to JSON object
- **Json Object To Rotator**: Convert JSON object to FRotator
- **Transform To Json Object**: Convert FTransform to JSON object
- **Json Object To Transform**: Convert JSON object to FTransform
- **Color To Json Object**: Convert FLinearColor to JSON object
- **Json Object To Color**: Convert JSON object to FLinearColor

## Usage Examples

### Creating and Serializing JSON Data

```cpp
// Create a JSON object
FJsonFlowObject PlayerData = UJsonFlowBlueprintLibrary::CreateJsonObject();

// Set player information
UJsonFlowBlueprintLibrary::SetStringField(PlayerData, "Name", "Player1");
UJsonFlowBlueprintLibrary::SetIntegerField(PlayerData, "Level", 25);
UJsonFlowBlueprintLibrary::SetBooleanField(PlayerData, "IsOnline", true);

// Convert player position to JSON
FVector PlayerPosition = FVector(100.0f, 200.0f, 300.0f);
FJsonFlowObject PositionJson = UJsonFlowBlueprintLibrary::VectorToJsonObject(PlayerPosition);
UJsonFlowBlueprintLibrary::SetObjectField(PlayerData, "Position", PositionJson);

// Serialize to JSON string
FString JsonString = UJsonFlowBlueprintLibrary::JsonObjectToString(PlayerData, true);
```

### Parsing and Reading JSON Data

```cpp
// Parse JSON string
FString JsonInput = "{\"Name\":\"Player1\",\"Level\":25,\"IsOnline\":true}";
FJsonFlowObject ParsedData;
bool bSuccess = UJsonFlowBlueprintLibrary::ParseJsonString(JsonInput, ParsedData);

if (bSuccess)
{
    // Read values
    FString PlayerName;
    int32 PlayerLevel;
    bool bIsOnline;
    
    UJsonFlowBlueprintLibrary::GetStringField(ParsedData, "Name", PlayerName);
    UJsonFlowBlueprintLibrary::GetIntegerField(ParsedData, "Level", PlayerLevel);
    UJsonFlowBlueprintLibrary::GetBooleanField(ParsedData, "IsOnline", bIsOnline);
}
```

### Working with JSON Arrays

```cpp
// Create a JSON array
FJsonFlowArray ScoreArray = UJsonFlowBlueprintLibrary::CreateJsonArray();

// Add scores
UJsonFlowBlueprintLibrary::AddIntegerToArray(ScoreArray, 1000);
UJsonFlowBlueprintLibrary::AddIntegerToArray(ScoreArray, 1500);
UJsonFlowBlueprintLibrary::AddIntegerToArray(ScoreArray, 2000);

// Add array to main object
UJsonFlowBlueprintLibrary::SetArrayField(PlayerData, "HighScores", ScoreArray);

// Read array values
int32 FirstScore;
UJsonFlowBlueprintLibrary::GetIntegerFromArray(ScoreArray, 0, FirstScore);
```

## Installation

1. Copy the JsonFlow plugin folder to your project's `Plugins` directory
2. Regenerate project files
3. Build your project
4. Enable the JsonFlow plugin in the Plugin Manager

## Blueprint Categories

All JsonFlow functions are organized in Blueprint categories:
- **JsonFlow|Parse**: JSON parsing functions
- **JsonFlow|Serialize**: JSON serialization functions
- **JsonFlow|Object**: JSON object operations
- **JsonFlow|Object|Set**: Setting values in JSON objects
- **JsonFlow|Object|Get**: Getting values from JSON objects
- **JsonFlow|Array**: JSON array operations
- **JsonFlow|Array|Add**: Adding values to JSON arrays
- **JsonFlow|Array|Get**: Getting values from JSON arrays
- **JsonFlow|Value**: JSON value operations
- **JsonFlow|Convert**: Blueprint type conversions

## Requirements

- Unreal Engine 5.2 or later
- C++ project (for compilation)
