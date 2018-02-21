---
title: "自訂文件屬性概觀 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 672eaf3ed82a80983b919a37b2aeff4c99621f43
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2018
---
# <a name="custom-document-properties-overview"></a>Custom Document Properties Overview

當您建置文件層級專案時，Visual Studio 會將兩個自訂屬性加入至專案中的文件：\_組件位置和\_AssemblyName。 當使用者開啟文件時，Microsoft Office 應用程式會檢查這些自訂文件屬性。 如果它們存在文件中，應用程式載入[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，以便啟動自訂。 如需詳細資訊，請參閱[Office 方案的架構在 Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

此屬性包含的介面中的 Office 方案載入器元件的 CLSID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 CLSID 值是 4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B。 您應該永遠不會變更此值。

## <a name="assemblylocation"></a>\_AssemblyLocation

此屬性包含自訂提供詳細的部署資訊清單的字串。 如需詳細資訊清單的詳細資訊，請參閱[應用程式和部署資訊清單在 Office 方案中](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

 The_AssemblyLocation 屬性值可以有不同的格式，方案部署的方式：

- 如果從網站、 UNC 路徑或 CD 或 USB 磁碟機上安裝發行方案，則 _AssemblyLocation 屬性具有格式*DeploymentManifestPath*|*方案識別碼已*。 下列字串是一個範例：

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- 如果您要執行，或從 Visual Studio 方案進行偵錯，_AssemblyLocation 屬性具有格式*DeploymentManifestName*|*方案識別碼已*| vstolocal。 下列字串是一個範例：

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *方案識別碼已*是 GUID，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]用來識別解決方案。 *方案識別碼已*會建置專案時自動產生。 **Vstolocal**詞彙來表示[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]從相同的資料夾和文件應該在載入組件。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中的 Office 方案的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
[應用程式和部署資訊清單在 Office 方案中](../vsto/application-and-deployment-manifests-in-office-solutions.md) 
 [How to： 使用 ClickOnce 發行 Office 方案](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
[How to： 建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)
