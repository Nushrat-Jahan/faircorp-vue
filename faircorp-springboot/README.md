# Faircorp

## API Documentation
### Windows Endpoints
#### Get Windows List:
- Request Type: GET
- Endpoint: /api/windows

#### Get Window With A Specific ID:
- Request Type: GET
- Endpoint: /api/windows/{windowId}
- {windowId}: A Long Integer

#### Get List Of Windows That Belongs To The Same Room:
- Request Type: GET
- Endpoint: /api/windows/rooms/{roomId}
- {roomId}: A Long Integer
#### Create A New Window:
- Request Type: POST
- Endpoint: /api/windows
- Body:
    ```json
    {
      "id": 0,
      "name": "string",
      "roomId": 0,
      "roomName": "string",
      "windowStatus": "CLOSED"
    }
    ```

#### Delete A Window:
- Request Type: DELETE
- Endpoint: /api/windows/{windowId}
- {windowId}: A Long Integer

#### Update A Window Status( OPEN <-> CLOSED):
- Request Type: PUT
- Endpoint: /api/windows/{windowId}/switch
- {windowId}: A Long Integer

### Heaters Endpoints:
#### Get Heaters List:
- Request Type: GET
- Endpoint: /api/heaters

#### Get Heater With A Specific ID:
- Request Type: GET
- Endpoint: /api/heaters/{heaterId}
- {heaterId}: A Long Integer

#### Create A New Heater:
- Request Type: POST
- Endpoint: /api/heaters
- Body:
    ```json
    {
      "heaterStatus": "OFF",
      "id": 0,
      "name": "string",
      "power": 0,
      "roomId": 0,
      "roomName": "string"
    }
    ```
#### Delete A Heater:
- Request Type: DELETE
- Endpoint: /api/heaters/{heaterId}
- {heaterId}: A Long Integer

#### Update A Heater Status(ON <-> OFF):
- Request Type: PUT
- Endpoint: /api/heaters/{heaterId}/switch
- {heaterId}: A Long Integer

### Rooms Endpoints:

#### Get Rooms List:
- Request Type: GET
- Endpoint: /api/rooms

#### Get Room With A Specific ID:
- Request Type: GET
- Endpoint: /api/rooms/{roomId}
- {roomId}: A Long Integer

#### Get List Of Rooms That Belongs To The Same Building
- Request Type: GET
- Endpoint: /api/rooms/buildings/{buildingId}
- {buildingId}: A long Integer

#### Update Heaters Status Inside A Room (ON <-> OFF):
- Request Type: PUT
- Endpoint: /api/rooms/{roomId}/switchHeaters
- {roomId}: A Long Integer

#### Update Windows Status Inside A Room (CLOSED <-> OPEN):
- Request Type: PUT
- Endpoint: /api/rooms/{roomId}/switchWindows
- {roomId}: A Long Integer

#### Create A New Room:
- Request Type: POST
- Endpoint: /api/rooms
- Body:
    ```json
    {
      "currentTemperature": 0,
      "floor": 0,
      "id": 0,
      "name": "string",
      "targetTemperature": 0
    }
    ```

#### Delete A Room:
- Request Type: DELETE
- Endpoint: /api/rooms/{roomId}
- {roomId}: A Long Integer

### Buildings Endpoints:

#### Get Buildings List:
- Request Type: GET
- Endpoint: /api/buildings

#### Get Building With A Specific ID:
- Request Type: GET
- Endpoint: /api/buildings/{buildingId}
- {buildingId}: A Long Integer

#### Create A New Building:
- Request Type: POST
- Endpoint: /api/buildings
- Body:
    ```json
    {
      "id": 0,
      "outsideTemperature": 0
    }
    ```
#### Delete A Building:
- Request Type: DELETE
- Endpoint: /api/buildings/{buildingId}
- {buildingId}: A Long Integer

### NOTES:
- If you delete a room all windows and heaters inside this room will be deleted
- If you delete a building all rooms inside the building will be deleted

### To TEST the API you can use SWAGGER UI:
```bash
# dependency
implementation 'io.springfox:springfox-boot-starter:3.0.0'
```

