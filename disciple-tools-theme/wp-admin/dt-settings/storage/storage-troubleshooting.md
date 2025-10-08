# S3 Storage Troubleshooting Guide

This guide helps you resolve common issues with S3 storage configuration and usage in Disciple.Tools.

## Common Issues Overview

S3 storage issues typically fall into these categories:
- Connection and authentication problems
- File upload failures
- Access and permission errors
- Performance and timeout issues
- Configuration mistakes

## Connection Issues

### Test Connection Fails

**Symptoms**: The "Test Connection" button returns an error or times out.

**Common Causes**:
- Incorrect credentials
- Wrong endpoint URL
- Network connectivity issues
- Bucket doesn't exist
- Insufficient permissions

**Solutions**:

1. **Verify Credentials**
   - Double-check Access Key and Secret Key
   - Ensure keys are active and not expired
   - Click Save, then use the Test Connection button in Disciple.Tools

2. **Check Endpoint URL**
   - For AWS S3: Leave endpoint blank or use `https://s3.amazonaws.com`
   - For MinIO: Use `http://your-server:9000` or `https://your-server:9000`
   - For Backblaze B2: Use `https://s3.us-west-000.backblazeb2.com`
   - For Cloudflare R2: Use `https://your-account-id.r2.cloudflarestorage.com`

3. **Verify Bucket Exists**
   - Check bucket name spelling
   - Ensure bucket is in the correct region
   - Verify bucket is accessible with your credentials

### Authentication Errors

**Error Messages**:
- "Access Denied"
- "Invalid credentials"
- "Signature mismatch"

**Solutions**:

1. **Regenerate Access Keys**
   - Create new access keys in your provider console
   - Update credentials in Disciple.Tools settings
   - Test connection with new keys

2. **Check IAM Permissions** (AWS)
   - Ensure user has the following required S3 permissions
      - Create Objects
      - Read Objects
      - Update Objects
      - Delete Objects
   - Verify bucket policy allows access
   - Check for conflicting policies

3. **Verify Secret Key**
   - Ensure secret key is copied completely
   - Check for extra spaces or characters
   - Try re-entering the secret key

## Upload Errors

### File Upload Fails

**Symptoms**: Files fail to upload with error messages or timeouts.

**Common Causes**:
- File size exceeds limits
- Unsupported file type
- Network connectivity issues
- Insufficient storage space
- Permission problems

**Solutions**:

1. **Check File Size**
   - Verify the file is under your site's upload limit (WordPress/server setting)
   - Compress large images before upload
   - Use appropriate file formats

2. **Verify File Type**
   - Ensure file type is supported
   - Check file extension matches content
   - Try converting to supported format

3. **Test Network Connection**
   - Check internet speed and stability
   - Try uploading from different network
   - Test with smaller files first

4. **Check Storage Space**
   - Verify S3 bucket has available space
   - Check account storage limits
   - Monitor storage usage

### Upload Timeout

**Symptoms**: Uploads start but never complete or timeout.

**Solutions**:

1. **Increase Timeout Settings**
   - Check server timeout configurations
   - Adjust PHP upload limits if possible
   - Use smaller file sizes

2. **Optimize File Size**
   - Compress images before upload
   - Use appropriate image formats
   - Split large files if necessary

3. **Check Server Resources**
   - Monitor server memory usage
   - Check disk space on server
   - Verify PHP memory limits

## Access and Permission Issues

### Files Not Accessible

**Symptoms**: Uploaded files cannot be viewed or downloaded.

**Common Causes**:
- Incorrect bucket permissions
- Missing CORS configuration
- Presigned URL generation issues
- File path problems

**Solutions**:

1. **Check Bucket Permissions**
   - Ensure the credentials can PutObject, GetObject, DeleteObject, and ListBucket for the bucket
   - Check object-level permissions if using bucket policies
   - Avoid making the bucket public; Disciple.Tools serves files to authorized users

2. **Configure [Cross-Origin Resource Sharing (CORS)](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)** (if needed)
   - Most flows are server-side and do not require CORS
      - Note: See your server-side provider's documentation regarding updating CORS setup; which is beyond the scope of this documentation.
   - If your setup makes browser-direct requests to the endpoint, allow GET and HEAD from your site origin
   - Keep rules minimal; avoid wildcarding credentials

3. **Verify File Paths**
   - Check file keys in S3 console
   - Ensure consistent naming conventions
   - Verify site ID prefixes

### Permission Denied Errors

**Error Messages**:
- "Access Denied"
- "Forbidden"
- "Insufficient permissions"

**Solutions**:

1. **Review IAM Policies** (AWS)
   - Ensure policies include required actions
   - Check resource ARNs are correct
   - Verify policy syntax

2. **Check Bucket Policies**
   - Verify bucket policy allows access
   - Check for conflicting policies
   - Ensure proper principal configuration

3. **Test with Minimal Permissions**
   - Create user with minimal required permissions
   - Test each permission individually
   - Gradually add permissions as needed

## Configuration Issues

### Wrong Provider Settings

**Symptoms**: Connection works but files aren't stored correctly.

**Common Causes**:
- Incorrect path-style endpoint setting
- Wrong region configuration
- Provider-specific settings missing

**Solutions**:

1. **Path-Style Endpoint**
   - Commonly required for MinIO
   - Not required for AWS S3, Backblaze B2, or Cloudflare R2
   - Only enable if your provider requires it

2. **Region Configuration**
   - Use correct region for your bucket
   - For some providers, use `auto` or `us-east-1`
   - Check provider documentation for region requirements

3. **Provider-Specific Settings**
   - Review provider documentation
   - Check for additional required settings
   - Verify endpoint URLs are correct

### Multi-Site Configuration Issues

**Symptoms**: Issues with multiple sites sharing storage.

**Solutions**:

1. **Site ID Prefixing**
   - Disciple.Tools automatically prefixes object keys with the current site ID
   - No manual action is needed to separate sites when sharing a bucket
   - In your provider's bucket dashboard, you will see keys starting with your site ID

2. **Shared vs. Separate Buckets**
   - Consider using separate buckets for each site
   - Implement proper access controls
   - Monitor cross-site access

## Performance Issues

### Slow Uploads

**Symptoms**: Files upload but take unusually long time.

**Solutions**:

1. **Check Network Speed**
   - Test upload speed to S3 directly
   - Compare with other cloud services
   - Check for network throttling


2. **Optimize File Sizes**
   - Compress images before upload
   - Use appropriate file formats
   - Consider progressive upload for large files

3. **Server Configuration**
   - Increase PHP memory limits
   - Optimize server settings
   - Check for resource constraints

### High Storage Costs

**Symptoms**: Unexpected charges from S3 provider.

**Solutions**:

1. **Monitor Storage Usage**
   - Check bucket size and object count
   - Review access patterns
   - Identify large or unused files


2. **Implement Lifecycle Policies**
   - Set up automatic deletion of old files
   - Move infrequently accessed files to cheaper storage
   - Compress files when possible

3. **Optimize File Management**
   - Remove duplicate files
   - Compress existing files
   - Implement file retention policies

## Error Messages Reference

### Common Error Messages and Solutions

| Error Message | Likely Cause | Solution |
|---------------|--------------|----------|
| "Access Denied" | Wrong credentials or permissions | Check credentials and IAM policies |
| "Bucket not found" | Wrong bucket name or region | Verify bucket name and region |
| "Signature mismatch" | Wrong secret key | Regenerate and re-enter secret key |
| "Request timeout" | Network or server issues | Check network and server resources |
| "File too large" | Exceeds size limits | Compress file or increase limits |
| "Invalid file type" | Unsupported format | Use supported file format |


## Getting Additional Help

### When to Contact Support

Contact your system administrator or Disciple.Tools support if:

- All troubleshooting steps have been attempted
- Issues persist after configuration changes
- Error messages are unclear or unusual
- Multiple users are affected

### Information to Provide

When seeking help, include:

- Exact error messages
- Steps to reproduce the issue
- Configuration details (without credentials)
- Browser and device information
- Network environment details

### Self-Service Resources

- [Storage Setup Guide](./storage-setup.md)
- [Storage Usage Guide](./storage-usage.md)
- [Main Storage Documentation](./storage.md)
- Provider-specific documentation
- Disciple.Tools community forums

---

## Next Steps

- [Review storage setup →](./storage-setup.md)
- [Learn about storage features →](./storage-usage.md)
- [Return to main storage documentation →](./storage.md)
