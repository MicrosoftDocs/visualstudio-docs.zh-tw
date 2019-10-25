---
title: 如何：安裝視覺化檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c9c2fa8a8fb300c3b7eb702ae3efd216e17141a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733098"
---
# <a name="how-to-install-a-visualizer"></a>如何：安裝視覺化檢視
建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。

> [!NOTE]
> 在 UWP 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。

### <a name="to-install-a-visualizer"></a>安裝視覺化檢視

1. 找出包含您已建置之視覺化檢視的 DLL。

2. 將該 DLL 複製至下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 如果要使用 Managed 視覺化檢視進行遠端偵錯，請將 DLL 複製到遠端電腦上的相同路徑中。

4. 重新啟動偵錯工作階段。

## <a name="see-also"></a>請參閱
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
- [如何：撰寫視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)