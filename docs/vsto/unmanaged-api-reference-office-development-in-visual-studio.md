---
title: 非受控 API 參考（Visual Studio 中的 Office 開發）
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c1616d24ae9b2c072df4e5708eb98e86611a83d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540981"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>非受控 API 參考（Visual Studio 中的 Office 開發）

從 2007 Microsoft Office 系統開始，Office 應用程式會使用[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)介面呼叫隨附的 VSTO 增益集載入器元件 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 這個元件是用來協助載入 managed VSTO 增益集。您可以藉由執行此介面來建立自己的 VSTO 增益集載入器元件。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>本節內容

[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)

COM 介面，您可以實作這個介面，在 Office 應用程式中載入和卸載 VSTO 增益集。
