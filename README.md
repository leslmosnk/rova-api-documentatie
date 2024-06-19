# ROVA API

The Dutch ROVA API, much like the garbage it handles, leaves developers navigating a landscape as unclear as a murky landfill. Despite playing a pivotal role in waste management across the Netherlands, ROVA has opted for a documentation strategy that's as sparse as an overfilled trash bin on collection day. For developers looking to integrate waste management functionalities, ROVA's lack of official API documentation can feel as frustrating as sorting through a bin of mixed recyclables without clear labels.

To fill this glaring gap, we have created this detailed documentation to help users navigate the complexities of the ROVA API. Here, you'll find guidance on scheduling waste collections, retrieving information about waste disposal guidelines, locating recycling centers, and accessing real-time data on waste collection services. Our goal is to ensure that, despite ROVA's oversight, you can efficiently utilize their API to enhance waste management processes, improve service delivery, and promote sustainability in your community.

## Waste Calendar

The Waste-Calendar endpoints allow users to retrieve information related to waste collection schedules. These endpoints do not require authentication, making it straightforward to access and integrate waste collection data.

### GET: Upcomming Collections

`https://www.rova.nl/api/waste-calendar/upcoming`

The upcoming collections endpoint allows users to retrieve a detailed schedule of upcoming waste collection dates for a specified address. This endpoint does not require authentication, making it easy to access and integrate waste collection data into your applications.

#### Query Parameters:

| Key         | Constraints                            | Description                                                                                                |
| ----------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| postalcode  | required, string                       | The postal code of the address.                                                                            |
| houseNumber | required, string                       | The house number of the address.                                                                           |
| _addition_  | optional, string                       | Additional address information (e.g., apartment number).                                                   |
| _take_      | optional, integer, default: 3, max: 50 | The number of upcoming collection events to retrieve. Use a high value like 50 to get all upcoming events. |

#### Response:

```json
{
    "id": integer,
    "date": DateTime,
    "wasteType": {
        "id": integer,
        "code": string,
        "title": string,
        "icon": string,
        "notificationTitle": string,
        "notificationText": string,
        "notificationTitleSameDay": string,
        "notificationTextSameDay": string
    },
    "isIrregular": boolean,
}
```

### GET: Yearly Collections

`https://www.rova.nl/api/waste-calendar/year`

The yearly collections endpoint allows users to retrieve the waste collection schedule for an entire year for a specified address. This endpoint does not require authentication, making it accessible for users who need comprehensive waste collection data for planning purposes.

#### Query Parameters:

| Key         | Constraints                              | Description                                                   |
| ----------- | ---------------------------------------- | ------------------------------------------------------------- |
| postalcode  | required, string                         | The postal code of the address.                               |
| houseNumber | required, string                         | The house number of the address.                              |
| _addition_  | optional, string                         | Additional address information (e.g., apartment number).      |
| _year_      | optional, integer, default: current year | The year for which to retrieve the waste collection schedule. |

#### Response:

```json
{
    "id": integer,
    "date": DateTime,
    "wasteType": {
        "id": integer,
        "code": string,
        "title": string,
        "icon": string,
        "notificationTitle": string,
        "notificationText": string,
        "notificationTitleSameDay": string,
        "notificationTextSameDay": string
    },
    "isIrregular": boolean,
}
```

### GET: Yearly Collections PDF

`https://www.rova.nl/api/waste-calendar/year/pdf`

The PDF collection schedule endpoint allows users to retrieve a user-friendly PDF containing the waste collection schedule for a specified address and year. This endpoint provides a convenient way to access and share waste collection information in a printable format. No authentication is required for this endpoint.

#### Query Parameters:

| Key         | Constraints                              | Description                                                   |
| ----------- | ---------------------------------------- | ------------------------------------------------------------- |
| postalcode  | required, string                         | The postal code of the address.                               |
| houseNumber | required, string                         | The house number of the address.                              |
| _addition_  | optional, string                         | Additional address information (e.g., apartment number).      |
| _year_      | optional, integer, default: current year | The year for which to retrieve the waste collection schedule. |

#### Response:

The response is a PDF file containing the waste collection schedule for the specified address and year.

---

# Feedback and contributions

While this documentation aims to provide a comprehensive overview of the available endpoints and parameters, it's possible that updates or additional features may have been introduced since its creation. As a result, your feedback is invaluable. If you encounter any issues or have suggestions for improvement, please consider send
