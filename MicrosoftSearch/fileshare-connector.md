---
title: "File share Microsoft Graph connector"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NoIndex
description: "Set up the File share Graph connector for Microsoft Search"
---
<!---Previous ms.author: rusamai --->

# File share Microsoft Graph connector

The File share Microsoft Graph connector allows users in your organization to search on-premise Windows file shares.

> [!NOTE]
> Read the [**Setup for your Microsoft Graph connector**](configure-connector.md) article to understand the general connectors setup process.

## Before you get started

### Install the Microsoft Graph connector agent

To index your Windows file shares, you must install and register the connector agent. See [Install the Microsoft Microsoft Graph connector agent](graph-connector-agent.md) to learn more.  

### Content requirements

### File types

Content of the following formats can be indexed and searched: DOC, DOCM, DOCX, DOT, DOTX, EML, GIF, HTML, JPEG, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS, and ZIP. Only the textual content of these formats is indexed. All multimedia content is ignored. For any file that doesn't belong to this format, the metadata alone is indexed.

### File size limits

The maximum supported file size is 100 MB. Files that exceed 100 MB aren't indexed. The maximum post-processed size limit is 4 MB. Processing stops when a file's size reaches 4 MB. Therefore, some phrases present in the file might not work for search.

## Step 1: Add a connector in the Microsoft 365 admin center

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

> [!NOTE]
> You can index up to twenty different file shares in a single connection. Enter one file share per line in the file shares text box area.

On the **Connect to data source** page, select **File share** and provide the name, connection ID, and description. On the next page, provide the path to the file share and select your previously installed Graph connector agent. Enter the credentials for a [Microsoft Windows](https://microsoft.com/windows) user account with read access to all the files in the file share.

### Preserve last access time

When the connector attempts to crawl a file, the "last access time" field in its metadata is updated. If you depend on that field for any archiving and backup solutions and you don't want to update it when the connector accesses it, you can configure this option in the **Advanced settings** page.

## Step 4: Limits for file indexing

While configuring a File Share connection, admin would have ability to limit files and folders from indexing. There would be multiple ways of doing it:

#### Based on File Types

Only the textual content of these formats is indexed: DOC, DOCM, DOCX, DOT, DOTX, EML, HTML, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS. For multimedia files and files that don't belong to this format, the only metadata is indexed.

#### Based on last modified date or number of days since last modification

#### Full network path of file/folder or regular expression to limit indexing

In the network path use the escape character (\\) before special characters like \\. Example: For the path \\\\CONTOSO\\FILE\\SHAREDFOLDER, correct way to input is  \\\\\\\\CONTOSO\\\\FILE\\\\SHAREDFOLDER

Rules for writing regular expression can be found [here](/dotnet/standard/base-types/regular-expression-language-quick-reference).

Admin would also be having ability to give an exception to the limit rule. Priority of exception rule will supersede Limit rules. In similar fashion, exception could be defined by giving folder/file path for the items we want to include in indexing.

![Limits and Exceptions.](media/file-connector/ExclusionRule.png)

## Step 5: Manage search permissions

You can restrict the permission to search for any file based on Share Access Control Lists or New Technology File System (NTFS) Access Control Lists, by selecting the desired option in **Manage search permissions** page. The user accounts and groups provided in these Access Control Lists must be managed by Active Directory (AD). If you're using any other system for user accounts management, you can select 'everyone' option, which lets users search for all the files without any access restrictions. However, when users try to open the file, access controls set at the source apply.

Windows by default provides 'Read' permission to 'Everyone' in Share ACLs when a folder is shared on network. By extension, if you're choosing Share ACLs in **Manage search permissions**, users will be able to search for all the files. If you want to restrict access, remove 'Read' access for 'Everyone' in file shares and provide access only to the desired users and groups. The connector then reads these access restrictions and applies them to search.

You can choose Share ACLs only if the share path you provided follows UNC path format. You can create a path in UNC format by going to 'Advanced Sharing' under 'Sharing' option.

:::image type="content" source="media/file-connector/file-advanced-sharing.png" alt-text="Advanced sharing." lightbox="media/file-connector/file-advanced-sharing.png":::

## Step 6: Assign property labels

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 7: Manage schema

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 8: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 9: Review connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->

<!---## Limitations-->
<!---Insert limitations for this data source-->
