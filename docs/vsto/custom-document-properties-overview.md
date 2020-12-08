---
title: 自訂文件屬性總覽
description: 瞭解當您建立檔層級專案時，Visual Studio 會將兩個自訂屬性加入至專案中的檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8c30e0b3253e19316eed24fa26500cd55a3dd515
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847789"
---
# <a name="custom-document-properties-overview"></a>自訂文件屬性總覽

當您建立檔層級專案時，Visual Studio 會將兩個自訂屬性加入至專案中的檔： \_ AssemblyLocation 和 \_ AssemblyName。 當使用者開啟檔時，Microsoft Office 的應用程式會檢查這些自訂文件屬性。 如果它們存在於檔中，應用程式會載入 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ，以啟動自訂。 如需詳細資訊，請參閱 [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_集

這個屬性包含的 Office 方案載入器元件中的介面 CLSID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 CLSID 值為4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B。 您永遠不應該變更此值。

## <a name="_assemblylocation"></a>\_AssemblyLocation

此屬性包含一個字串，該字串提供自訂的部署資訊清單詳細資料。 如需資訊清單的詳細資訊，請參閱 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)。

 \_AssemblyLocation 屬性值可以有不同的格式，視解決方案的部署方式而定：

- 如果從網站、UNC 路徑或 CD 或 USB 磁片磁碟機發行方案，則 _AssemblyLocation 屬性的格式為 *DeploymentManifestPath* | *SolutionID*。 下列字串為範例：

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- 如果您是從 Visual Studio 執行或錯用方案，則 _AssemblyLocation 屬性的格式為 *DeploymentManifestName* | *SolutionID*| vstolocal。 下列字串為範例：

     Excelworkbook1.xlsx.log vsto | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionID* 是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 用來識別方案的 GUID。 當您建立專案時，會自動產生 *SolutionID* 。 **Vstolocal** 字詞會向指出 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 應該從與檔相同的資料夾載入元件。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [如何：使用 ClickOnce 發行 Office 方案](/previous-versions/bb386095(v=vs.110))
- [如何：建立和修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)