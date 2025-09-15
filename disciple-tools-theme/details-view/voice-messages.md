# Voice Messages

Learn how to record, store, and manage voice messages in Disciple.Tools using S3 storage.

## Overview

Voice messages allow you to record and attach audio messages to records in Disciple.Tools. When S3 storage is enabled, voice messages are securely stored in your configured S3 bucket, ensuring privacy and accessibility only to authorized users.


## Voice Message Features

### Key Capabilities

- **Audio Recording**: Record voice messages directly in the browser
- **Secure Storage**: Messages stored privately in S3 bucket
- **Playback Controls**: Listen to recorded messages with standard audio controls
- **File Management**: Save, delete, or re-record messages
- **Access Control**: Only authorized users can listen to messages

![Voice Message Features](./imgs/details-view/voice-message-features.png)

### Supported Audio Formats

Voice messages are automatically converted and stored in optimized formats:

- **Primary Format**: MP3 (compressed for efficient storage)
- **Quality**: Optimized for voice clarity
- **File Size**: Compressed to minimize storage usage
- **Compatibility**: Plays in all modern browsers and devices


## Recording Voice Messages

### Accessing Voice Recording

Voice recording functionality is available in several locations:

1. **Comments Section**: Record voice messages as part of comments
2. **Activity Log**: Add voice messages to activity entries


### Recording Interface

The voice recording interface includes:

- **Record Button**: Start and stop recording
- **Visual Indicators**: Show recording status and duration
- **Audio Waveform**: Visual representation of audio levels
- **Playback Controls**: Listen to recorded messages
- **File Management**: Save, delete, or re-record options

![Voice Message Interface](./imgs/details-view/voice-message-interface.png)

### Recording Process

#### Step 1: Start Recording

1. Navigate to the location where you want to add a voice message
2. Click the voice recording button or microphone icon
3. Grant microphone permissions when prompted by your browser
4. The recording interface will appear


#### Step 2: Record Your Message

1. **Click Record**: Press the record button to start recording
2. **Speak Clearly**: Talk into your microphone at normal volume
3. **Monitor Levels**: Watch the audio level indicators
4. **Stop Recording**: Click stop when finished


#### Step 3: Review and Save

1. **Playback**: Listen to your recorded message
2. **Re-record**: Click record again if you want to start over
3. **Save**: Click save to attach the message to the record
4. **Cancel**: Click cancel to discard the recording


## Voice Message Storage

### S3 Storage Benefits

Voice messages stored in S3 benefit from:

- **Private Storage**: Messages are not publicly accessible
- **Encrypted Transfer**: All recordings use secure HTTPS connections
- **Access Control**: Only authorized users can listen to messages
- **Secure URLs**: Temporary, time-limited access links
- **Audit Trail**: All message access is logged


### File Organization

Voice messages are organized in your S3 bucket:

```
your-bucket/
├── site-id/
│   ├── contacts/
│   │   ├── audio-recording-123-abc
│   └── other-record-types/
```

This organization ensures:
- **Message Isolation**: Each record's messages are separated
- **Easy Management**: Clear structure for administrators
- **Privacy Protection**: Messages are not mixed between records


## Playback and Management

### Listening to Voice Messages

Once recorded, voice messages can be played back using:

1. **Inline Player**: Click the play button next to the message

![Voice Message Playback](./imgs/details-view/voice-message-playback.png)

### Playback Controls

The voice message player includes standard audio controls:

- **Play/Pause**: Start and stop playback
- **Progress Bar**: Shows current position and allows seeking
- **Volume Control**: Adjust playback volume
- **Time Display**: Shows current time and total duration


### Message Management

You can manage voice messages through several actions:

- **Listen**: Play the message
- **Download**: Save to your device
- **Delete**: Remove the message (with confirmation)
- **Re-record**: Replace with a new recording

## Mobile Voice Recording

### Mobile-Specific Features

Voice recording on mobile devices includes:

- **Touch-Friendly Interface**: Large buttons optimized for touch
- **Camera Integration**: Can be combined with photo capture
- **Responsive Design**: Adapts to different screen sizes
- **Offline Handling**: Graceful handling of network issues


### Mobile Considerations

When recording on mobile devices:

- **Microphone Access**: Grant permission when prompted
- **Network Connection**: Ensure stable connection for upload
- **Battery Usage**: Recording may use more battery power
- **Storage Space**: Check available device storage

## Privacy and Security

### Voice Message Privacy

Voice messages are protected by several security measures:

- **Private Storage**: Messages stored in private S3 bucket
- **Access Control**: Only authorized users can listen
- **Encrypted Transfer**: All uploads and downloads use HTTPS
- **Temporary URLs**: Access links expire after 24 hours
- **Audit Logging**: All access is recorded


### Security Best Practices

When using voice messages:

- **Sensitive Information**: Avoid recording sensitive personal details
- **Access Permissions**: Ensure only authorized users can access messages
- **Regular Cleanup**: Remove old or unnecessary messages
- **Secure Devices**: Use secure devices for recording

## Troubleshooting Voice Messages

### Common Recording Issues

**Microphone Not Working**:
- Check browser permissions for microphone access
- Verify microphone is connected and working
- Try refreshing the page and granting permissions again

**Recording Quality Issues**:
- Speak clearly and at normal volume
- Check microphone positioning
- Ensure quiet environment for recording

**Upload Failures**:
- Check internet connection stability
- Verify S3 storage is properly configured
- Try recording a shorter message

### Browser Compatibility

Voice recording requires modern browser support for:

- **Web Audio API**: For recording functionality
- **MediaRecorder API**: For audio capture
- **Microphone Access**: For device permissions

Supported browsers:
- **Chrome**: Full support
- **Firefox**: Full support
- **Safari**: Full support (iOS 14.3+)
- **Edge**: Full support

### Error Messages

Common error messages and solutions:

| Error Message | Cause | Solution |
|---------------|-------|----------|
| "Microphone access denied" | Browser permission issue | Grant microphone permission |
| "Recording failed" | Technical issue | Refresh page and try again |
| "Upload failed" | Network or storage issue | Check connection and retry |
| "File too large" | Recording too long | Record shorter message |

## Best Practices

### Recording Best Practices

1. **Clear Speech**: Speak clearly and at normal volume
2. **Quiet Environment**: Record in a quiet location
3. **Appropriate Length**: Keep messages concise and relevant
4. **Test Recording**: Listen to your message before saving
5. **Professional Tone**: Use appropriate language and tone


### Message Management

- **Regular Review**: Periodically review and clean up old messages
- **Appropriate Content**: Ensure messages contain appropriate content
- **Access Control**: Be mindful of who can access your messages
- **Backup Important Messages**: Download critical messages for backup

## Integration with Other Features

### Comments and Activity

Voice messages integrate seamlessly with:

- **Comments**: Add voice messages to comment threads
- **Activity Log**: Include voice messages in activity entries
- **Notifications**: Users can be notified of new voice messages
- **Search**: Voice messages can be searched and filtered


### Record Types

Voice messages can be attached to various record types:

- **Contacts**: Personal voice messages for contacts
- **Groups**: Group voice announcements or updates
- **Users**: Internal voice communications
- **Custom Records**: Any custom record type that supports voice messages

---

## Related Documentation

- [S3 Storage Settings](../wp-admin/dt-settings/storage.md) - Learn about S3 storage configuration
- [S3 Storage Setup Guide](../wp-admin/dt-settings/storage-setup.md) - Detailed setup instructions
- [S3 Storage Usage Guide](../wp-admin/dt-settings/storage-usage.md) - User interface features
- [Uploading Files to Records](./uploading-files.md) - General file upload documentation
- [S3 Storage Troubleshooting](../wp-admin/dt-settings/storage-troubleshooting.md) - Common issues and solutions
