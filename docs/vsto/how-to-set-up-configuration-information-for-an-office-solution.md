---
title: 設定 Office 方案的設定資訊
description: 瞭解如何使用設定檔來設定 Microsoft Office 解決方案的特定設定。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da3a08ad9b3f6c78a10891e7d8ef2093ab46305d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927700"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>如何：設定 Office 方案的設定資訊
  您可以使用設定檔來設定 Office 方案的特定設定。 您可以指定設定，例如元件系結原則、遠端物件、偵錯工具和追蹤設定。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>將設定檔新增至 Office 專案

1. 在 [專案] 功能表上，按一下 [加入新項目]。

2. 在 [ **類別目錄** ] 窗格中，按一下 **[一般**]。

3. 在 [ **範本** ] 窗格中，選取 [ **應用程式佈建檔**]。

4. 在 [ **名稱** ] 方塊中，輸入與元件 *和副檔名相同的名稱。* 例如，名為 *ExcelWorkbook1.dll* 的 Excel 專案元件的設定檔會命名為 *ExcelWorkbook1.dll.config*。

5. 按一下 **[新增]** 。

6. 根據應用程式佈建檔架構建立設定檔。 如需詳細資訊，請參閱 [.NET Framework 的設定檔架構](/dotnet/framework/configure-apps/file-schema/index)。

   使用設定檔與 Office 專案沒有任何特殊考慮。

## <a name="see-also"></a>另請參閱
- [.NET Framework 的設定檔架構](/dotnet/framework/configure-apps/file-schema/index)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
