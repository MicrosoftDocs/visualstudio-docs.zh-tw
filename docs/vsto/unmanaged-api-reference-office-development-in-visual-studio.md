---
title: 非受控 API 參考 (Visual Studio 中的 Office 開發)
ms.date: 08/14/2019
ms.topic: conceptual
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
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551318"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>非受控 API 參考 (Visual Studio 中的 Office 開發)

從 2007 Microsoft Office 系統開始, Office 應用程式會使用[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)介面呼叫隨附[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的 VSTO 增益集載入器元件。 這個元件是用來協助載入 managed VSTO 增益集。您可以實作這個介面，來建立自己的 VSTO 增益集載入器元件。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>本節內容

[IManagedAddin 介面](../vsto/imanagedaddin-interface.md)

COM 介面，您可以實作這個介面，在 Office 應用程式中載入和卸載 VSTO 增益集。
