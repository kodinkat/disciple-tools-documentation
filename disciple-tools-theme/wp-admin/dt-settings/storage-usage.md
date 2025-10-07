# S3 Storage Usage Guide

This guide explains how users interact with S3 storage features in Disciple.Tools, including file uploads, image management, and voice message storage.

## Overview

When S3 storage is enabled, Disciple.Tools provides enhanced file upload capabilities that securely store media files in your configured S3 bucket. Users can upload profile pictures, attach images to comments, and record voice messages with confidence that their data is protected.


## File Upload Interface

The S3 storage system provides a modern, user-friendly upload interface with drag-and-drop functionality and real-time progress feedback.

### Upload Modal Features

When users click to upload files, they see a modal with the following features:

- **Drag-and-drop area** with visual feedback
- **File selection button** for traditional file browsing
- **Progress indicators** during upload
- **File type validation** with clear error messages
- **Success/error notifications** with appropriate actions


### Supported File Types

Disciple.Tools S3 storage supports various file types depending on the context:

#### Profile Pictures
- **Image formats**: `.gif`, `.jpg`, `.jpeg`, `.png`
- **Maximum size**: Varies by site's upload limit (WordPress/server setting)
- **Automatic thumbnails**: Generated for display optimization

#### Image Comments
- **Image formats**: `.gif`, `.jpg`, `.jpeg`, `.png`

#### Voice Messages
- **Audio formats**: Browser-supported formats (commonly WebM/Opus; may be OGG/Opus or MP4 depending on browser)
- **Recording quality**: Optimized for voice clarity
- **File size limits**: Varies by site's upload limit


## Drag and Drop Functionality

The upload interface supports modern drag-and-drop functionality for improved user experience.

### How Drag and Drop Works

1. **Visual Feedback**: The upload area changes appearance when files are dragged over it
2. **File Validation**: Only accepted file types can be dropped
3. **Multiple File Handling**: Single file uploads are enforced for security
4. **Error Prevention**: Invalid files are rejected with clear messages


### Browser Compatibility

Drag and drop functionality is available in modern browsers that support:
- HTML5 File API
- FormData API
- FileReader API

Older browsers will fall back to traditional file selection methods.

## File Type Validation

The system validates uploaded files to ensure security and compatibility.

### Validation Process

1. **File Extension Check**: Verifies the file has an accepted extension
2. **MIME Type Validation**: Confirms the file's actual type matches its extension
3. **Size Limit Check**: Ensures files don't exceed maximum size limits
4. **Content Scanning**: Basic security checks for malicious content


### Error Messages

When validation fails, users see clear, actionable error messages:

- **"Invalid file type"**: File format not supported
- **"File too large"**: Exceeds size limits
- **"Upload failed"**: Network or server issues
- **"Security check failed"**: Potential security concern

## Upload Progress and Feedback

Users receive real-time feedback during the upload process.

### Progress Indicators

- **Loading spinner**: Shows during file processing
- **Progress bar**: Displays upload completion percentage
- **Status messages**: Inform users of current operation
- **Success confirmation**: Confirms successful upload


### Upload States

The interface shows different states during the upload process:

1. **Ready**: Initial state, ready for file selection
2. **Processing**: File is being prepared for upload
3. **Uploading**: File is being transferred to S3
4. **Success**: Upload completed successfully
5. **Error**: Upload failed with error message

## Image Thumbnail Generation

For image uploads, the system automatically generates thumbnails for optimal display.

### Thumbnail Sizes

- **Small thumbnail**: 100px width for list views
- **Large thumbnail**: 1200px width for detailed views
- **Original image**: Full resolution for download


### Thumbnail Features

- **Automatic generation**: Created during upload process
- **Format preservation**: Maintains original image format
- **Quality optimization**: Balanced file size and image quality
- **Fallback handling**: Shows original if thumbnail generation fails

## File Management

Users can manage their uploaded files through various interfaces.

### File Actions

- **View/Download**: Access original files
- **Replace**: Upload new version of existing file
- **Delete**: Remove file from storage (with confirmation)
- **Share**: Generate secure access links


### Access Control

Files stored in S3 are protected by:
- **Presigned URLs**: Temporary, secure access links
- **User permissions**: Only authorized users can access files
- **Time-limited access**: URLs are secured and temporary
- **Site isolation**: Files are automatically organized by site ID prefix

## Voice Message Features

S3 storage enables secure voice message recording and playback.

### Recording Interface

- **Record button**: Start/stop voice recording
- **Playback controls**: Listen to recorded messages
- **Quality indicators**: Show recording status
- **File management**: Save, delete, or re-record


### Voice Message Storage

- **Secure storage**: Voice files stored privately in S3
- **Compression**: Optimized for voice quality and file size
- **Access control**: Only authorized users can listen
- **Retention**: Follows site data retention policies

## Mobile Experience

The S3 storage interface is optimized for mobile devices.

### Mobile Features

- **Touch-friendly interface**: Large buttons and touch targets
- **Responsive design**: Adapts to different screen sizes
- **Camera integration**: Direct photo capture and upload
- **Offline handling**: Graceful handling of network issues


### Mobile Considerations

- **File size limits**: Adjusted for mobile data usage
- **Image compression**: Automatic optimization for mobile
- **Progress indicators**: Clear feedback on slower connections
- **Error recovery**: Retry mechanisms for failed uploads

## Performance Optimization

The S3 storage system includes several performance optimizations.

### Upload Optimization

- **Efficient uploads**: Files uploaded directly to S3
- **Parallel processing**: Multiple operations handled simultaneously
- **Compression**: Images automatically compressed for thumbnails
- **Caching**: Frequently accessed files served through WordPress


### User Experience Enhancements

- **Background processing**: Uploads don't block other operations
- **Progress persistence**: Upload progress maintained across page refreshes
- **Error recovery**: Automatic retry for transient failures
- **Bandwidth adaptation**: Adjusts to available network speed

## Security Features

S3 storage provides enhanced security for sensitive files.

### Data Protection

- **Encryption in transit**: All uploads use HTTPS
- **Encryption at rest**: Files encrypted in S3 storage
- **Access logging**: File operations are logged through WordPress comment system
- **Audit trails**: File operations are tracked through WordPress activity


### Privacy Controls

- **Private storage**: Files not publicly accessible
- **User isolation**: Users can only access authorized files
- **Temporary URLs**: Time-limited access to files
- **Secure deletion**: Files permanently removed when deleted

---

## Next Steps

- [Set up S3 storage for your site →](./storage-setup.md)
- [Troubleshoot upload issues →](./storage-troubleshooting.md)
- [Return to main storage documentation →](./storage.md)
