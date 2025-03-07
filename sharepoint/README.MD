
## What This Playbook Does

1. **Authenticates with SharePoint** using your credentials
2. **Uploads all your files** (HTML, CSS, images) to a document library
3. **Creates a modern SharePoint page** with the title "Ansible Automation Platform Report"
4. **Embeds your HTML report** in the page using an iframe
5. **Publishes the page** so it's visible to users with appropriate permissions

## How to Use This Playbook

1. **Update the variables at the top**:
   ```yaml
   sharepoint_site: "https://your-organization.sharepoint.com/sites/YourSiteName"
   sharepoint_document_library: "Shared Documents/Ansible Reports"
   sharepoint_username: "your_email@your-organization.com"
   ```

2. **Set your password as an environment variable**:
   ```bash
   export SHAREPOINT_PASSWORD='your-password-here'
   ```

3. **Run the playbook**:
   ```bash
   ansible-playbook sharepoint_page_creation.yml
   ```

4. **Access your report** at the URL displayed at the end of the playbook run.

## Benefits of This Approach

- **SharePoint Integration**: The report is properly integrated into your SharePoint site navigation
- **Permissions Management**: Uses SharePoint's permission system
- **Visual Integration**: Appears as part of your SharePoint site
- **Responsive Layout**: The iframe adjusts to fit the page width
- **Minimal Configuration**: No need to configure web servers or special permissions

## Important Notes

1. **Modern Authentication**: This playbook uses username/password authentication. If your organization uses MFA or other advanced authentication methods, you might need to modify the authentication approach.

2. **SharePoint Version**: This is designed for SharePoint Online and SharePoint 2019+. Earlier versions may require modifications.

3. **Browser Compatibility**: The iframe approach works in all modern browsers.

4. **Content Security Policies**: Some SharePoint environments may have strict Content Security Policies that could affect embedded content.

If you encounter any issues with this approach, you might need to adjust based on your specific SharePoint environment's policies and configurations.


# More info on approach

Uploading files to SharePoint using Ansible is possible, though it requires leveraging SharePoint's REST API. Here's a playbook that should handle uploading your HTML report, CSS files, and images to SharePoint:

## How It Works

1. The playbook authenticates with Microsoft 365 to get an access token
2. Creates any necessary folders (like the CSS directory)
3. Uploads each file in the list to the specified location
4. Reports on successful uploads

## Potential Issues

- **Authentication**: If you're using MFA, you'll need to create an app password or use a service account
- **Permissions**: Ensure your account has write permissions to the document library
- **API Rate Limits**: For large uploads, be aware of SharePoint API rate limits

## Alternative Approaches

If this playbook doesn't work for your environment, you could also:

1. Use the Microsoft Graph API instead (more modern)
2. Use the PnP PowerShell modules (more reliable for SharePoint)
3. Use the SharePoint Client-Side Object Model (CSOM) with Python

Let me know if you need help adjusting this for your specific SharePoint environment!