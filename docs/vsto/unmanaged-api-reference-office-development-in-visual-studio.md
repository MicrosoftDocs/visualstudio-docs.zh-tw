---
title: "Unmanaged API 參考 （在 Visual Studio 中的 Office 程式開發） |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
ms.assetid: cdbc70b1-1f98-43dc-a619-07d805e53dce
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3a48af1199b041ef59c3e31e4e9496d78d21aec1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Unmanaged API 參考 (Visual Studio 中的 Office 程式開發)
  從 2007 Microsoft Office system 開始，Office 應用程式使用[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)介面呼叫的 VSTO 增益集載入器元件隨附於[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 這個元件可用來協助您載入 VSTO 增益集。您可以實作這個介面，來建立自己的 VSTO 增益集載入器元件。  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="in-this-section"></a>本節內容  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)  
 COM 介面，您可以實作這個介面，在 Office 應用程式中載入和卸載 VSTO 增益集。  
  
  