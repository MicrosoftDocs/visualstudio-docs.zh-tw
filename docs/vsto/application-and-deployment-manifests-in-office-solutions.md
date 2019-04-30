---
title: 在 Office 方案中的應用程式和部署資訊清單
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d22d58eb8a2264d5c7765a15726db556c7d5569f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942898"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>在 Office 方案中的應用程式和部署資訊清單
  應用程式資訊清單是提供資訊讓 Office 方案用來尋找及更新其組件的 XML 檔案。 應用程式資訊清單可以搭配部署資訊清單使用，部署資訊清單是伺服器上儲存的 XML 檔案，可提供尋找最新版應用程式資訊清單和組件所需的資訊。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Office 方案的資訊清單結構
 對於在 Visual Studio 中使用 Office 開發工具所建立的 Microsoft Office 方案，所有資訊清單都是根據標準的 ClickOnce 結構描述。 當您部署 Office 方案時，文件層級和 VSTO 增益集專案的應用程式資訊清單都位於 ClickOnce 快取。 部署資訊清單不會複製到用戶端電腦。

 應用程式和 Office 專案的部署資訊清單內容的相關資訊，請參閱[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)並[Deployment manifests for Office 方案](../vsto/deployment-manifests-for-office-solutions.md)。

## <a name="create-application-and-deployment-manifests"></a>建立應用程式和部署資訊清單
 應用程式資訊清單會在建置流程中自動建立。 每次建置文件層級專案時，部署資訊清單的位置會內嵌在文件中做為自訂文件屬性。 對於 VSTO 增益集，部署資訊清單的位置儲存在登錄中。

 如需詳細資訊**發行精靈**，請參閱[藉由使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

 如需有關如何清單搭配 Office 方案運作，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另請參閱

- [文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)
- [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)
- [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)