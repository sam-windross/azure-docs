---
title: Configure Advanced Threat Protection
description: Advanced Threat Protection detects anomalous database activities indicating potential security threats to the database in Azure SQL Database
services: sql-database
ms.service: sql-database
ms.subservice: security
ms.custom: seo-dt-2019, sqldbrb=1
ms.topic: how-to
author: rmatchoro
ms.author: ronmat
ms.reviewer: vanto
ms.date: 12/01/2020
---
# Configure Advanced Threat Protection for Azure SQL Database
[!INCLUDE[appliesto-sqldb](../includes/appliesto-sqldb.md)]

[Advanced Threat Protection](threat-detection-overview.md) for Azure SQL Database detects anomalous activities indicating unusual and potentially harmful attempts to access or exploit databases. Advanced Threat Protection can identify **Potential SQL injection**, **Access from unusual location or data center**, **Access from unfamiliar principal or potentially harmful application**, and **Brute force SQL credentials** - see more details in [Advanced Threat Protection alerts](threat-detection-overview.md#alerts).

You can receive notifications about the detected threats via [email notifications](threat-detection-overview.md#explore-detection-of-a-suspicious-event) or [Azure portal](threat-detection-overview.md#explore-alerts-in-the-azure-portal)

[Advanced Threat Protection](threat-detection-overview.md) is part of the [Microsoft Defender for SQL](azure-defender-for-sql.md) offering, which is a unified package for advanced SQL security capabilities. Advanced Threat Protection can be accessed and managed via the central Microsoft Defender for SQL portal.

## Set up Advanced Threat Protection in the Azure portal

1. Sign into the [Azure portal](https://portal.azure.com).
2. Navigate to the configuration page of the server you want to protect. In the security settings, select **Defender for Cloud**.
3. On the **Microsoft Defender for SQL** configuration page:

   - Enable **Microsoft Defender for SQL** on the server.
   - In **Advanced Threat Protection Settings**, provide the list of emails to receive security alerts upon detection of anomalous database activities in the **Send alerts to** text box.
   
   :::image type="content" source="media/azure-defender-for-sql/set-up-advanced-threat-protection.png" alt-text="set up advanced threat protection":::

## Set up Advanced Threat Protection using PowerShell

For a script example, see [Configure auditing and Advanced Threat Protection using PowerShell](scripts/auditing-threat-detection-powershell-configure.md).

## Next steps

- Learn more about [Advanced Threat Protection](threat-detection-overview.md).
- Learn more about [Advanced Threat Protection in SQL Managed Instance](../managed-instance/threat-detection-configure.md).  
- Learn more about [Microsoft Defender for SQL](azure-defender-for-sql.md).
- Learn more about [auditing](../../azure-sql/database/auditing-overview.md)
- Learn more about [Microsoft Defender for Cloud](../../security-center/security-center-introduction.md)
- For more information on pricing, see the [SQL Database pricing page](https://azure.microsoft.com/pricing/details/sql-database/)
