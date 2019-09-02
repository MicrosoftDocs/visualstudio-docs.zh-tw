---
title: HOW TO：安裝 Office 主要 interop 元件
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551801"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>HOW TO：安裝 Office 主要 interop 元件
  當您安裝 Office 時，請安裝 Microsoft Office 主要 Interop 組件 (PIA)。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>在安裝 Office 時安裝 PIA

1. 確定您有至少 2.0 版的 .NET Framework。

2. 安裝 Microsoft Office, 並確定已針對您想要擴充的應用程式選取 [.Net 程式設計**支援**] 功能 (這項功能包含在預設安裝中)。

    > [!WARNING]
    > 根據預設, 當您建立 PIA 時, 會將它內嵌在您的方案中, 如此您就不需要將 Pia 散發給使用者, 做為使用 VSTO 增益集或自訂的必要條件。

## <a name="see-also"></a>另請參閱
- [Office 主要 interop 元件](../vsto/office-primary-interop-assemblies.md)
- [如何：透過主要 interop 元件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [如何：設定電腦以開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [如何：安裝 Visual Studio Tools for Office 執行時間可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Office 方案開發總覽&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [開始&#40;在 Visual Studio 中進行 Office 開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
