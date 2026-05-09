# Shadow Realm Message Board

This is a cross-platform message board that allows registered users to see each other's messages across different devices and browsers.

## Features

- **Real-time messaging**: Messages appear instantly for all users
- **User presence**: See who's currently online
- **Media sharing**: Share images and videos with other users
- **Cross-platform compatibility**: Works on desktop, tablet, and mobile devices
- **Responsive design**: Adapts to different screen sizes

## Setup

1. The message board uses Firebase Realtime Database for storing messages and user status.
2. Firebase configuration is already included in the code.
3. No additional setup is required to use the basic functionality.

## Usage

1. Access the login page at `secret-login.html`
2. Log in with one of the following credentials:
   - Username: `admin`, Password: `shadow2025`
   - Username: `GothJesus`, Password: `Brown622`
3. Once logged in, you'll be redirected to the message board
4. Post messages, view other users' messages, and see who's online

## Technical Details

- Messages and user status are stored in Firebase Realtime Database
- Authentication is handled via localStorage for simplicity
- Media files are encoded as base64 and stored with the messages
- The application uses Firebase's real-time listeners to update the UI when data changes

## Cross-Platform Compatibility

The message board is designed to work on:
- Desktop browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Android Chrome)
- Tablets

Responsive design ensures that the UI adapts to different screen sizes and orientations.

## Security Note

This is a demonstration project. In a production environment, you would want to:
1. Implement proper authentication with Firebase Auth
2. Store media files in Firebase Storage instead of as base64 in the database
3. Add security rules to the Firebase database
4. Implement rate limiting and content moderation

## License

© 2025 Elora Borealis. All Rights Reserved.