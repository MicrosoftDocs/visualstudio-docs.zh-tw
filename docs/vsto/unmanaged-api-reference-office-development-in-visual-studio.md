---
title: Unmanaged 的 API 參考 （在 Visual Studio 中的 Office 程式開發）
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1ac4dfa9dd697993cffb527be521bd04c4c087ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991158"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Unmanaged 的 API 參考 （在 Visual Studio 中的 Office 程式開發）
  從 2007 Microsoft Office system 開始，Office 應用程式使用[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)介面呼叫 VSTO 增益集載入器元件隨附[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 此元件用來載入 managed VSTO 增益集。您可以實作這個介面，來建立自己的 VSTO 增益集載入器元件。  
  
> [!NOTE]  
>  想要開發解決方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集較小的使用量，相較於 VSTO 增益集和解決方案，而且您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3、 以及 XML 來建置。  
  
## <a name="in-this-section"></a>本節內容  
 [IManagedAddin 介面](../vsto/imanagedaddin-interface.md)  
 COM 介面，您可以實作這個介面，在 Office 應用程式中載入和卸載 VSTO 增益集。  
