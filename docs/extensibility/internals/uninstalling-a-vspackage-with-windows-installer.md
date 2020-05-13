---
title: 使用 Windows 安裝程式卸載 VS 包 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704270"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>使用 Windows Installer 解除安裝 VSPackage
在大多數情況下,Windows 安裝程式只需"撤消"安裝 VSPackage 時所做的"撤銷"即可卸載您的 VSPackage。 [安裝後必須運行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)中討論的自定義操作也必須在卸載後運行。 由於對 devenv.exe 的調用發生在安裝和卸載的「安裝Finalize」標準操作之前,因此自訂操作和安裝執行順序表條目同時適用於這兩種情況。

> [!NOTE]
> 卸載`devenv /setup`MSI 包後運行。

 通常,如果將自定義操作添加到 Windows 安裝程式包,則必須在卸載和回滾期間處理這些操作。 例如,如果將自定義操作添加到自動註冊 VSPackage,則還必須添加自定義操作來取消註冊它。

> [!NOTE]
> 使用者可以安裝 VSPackage,然後卸載與其整合的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本 。 以消除執行具有相依項的代碼的自訂操作,可以幫助確保 VSPackage 的卸載在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]這種情況下有效 。

## <a name="handling-launch-conditions-at-uninstall-time"></a>卸載時處理啟動條件
 啟動條件標準操作讀取啟動條件表的行,以在不符合條件時顯示錯誤消息。 由於啟動條件通常用於確保滿足系統要求,因此通常可以通過將`NOT Installed`條件 添加到啟動條件表的啟動條件行來跳過卸載期間的啟動條件。

 另一種方法是在卸載`OR Installed`期間添加不重要的啟動條件。 這可確保在卸載期間條件始終為 true,因此不會顯示啟動條件錯誤消息。

> [!NOTE]
> `Installed`是 Windows 安裝程式在檢測到您的 VSPackage 已安裝在系統上時設置的屬性。

## <a name="see-also"></a>另請參閱
- [Windows 安裝程式](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)
