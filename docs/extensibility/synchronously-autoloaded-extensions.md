---
title: 非同步自動載入延伸模組
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d23a19ad42f665f471274ee75f328056dd55b17d
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037107"
---
# <a name="synchronously-autoloaded-extensions"></a>非同步自動載入延伸模組

同步應用程式擴充功能的 Visual Studio 效能有負面影響，並且應該要改為使用非同步的 autoload 轉換。 從 Visual Studio 2019 Preview 2 開始，使用者會收到通知時延伸模組正在同步應用程式。 延伸模組會載入並正常運作。

![擴充功能的相容性警告](media/extension-compatibility-warning.png)

使用者可以：

- 按一下 **了解更多**來取得此資訊頁面。

- 按一下**管理效能**來開啟[效能管理員對話方塊](#performance-manager-dialog)顯示延伸模組和工具視窗的效能問題。

- 按一下 **不要再顯示此訊息**以關閉通知。 選擇此選項時，也可防止所有未來的通知，從同步應用程式擴充功能。 使用者仍會繼續其他的 Visual Studio 功能的相關通知。

## <a name="performance-manager-dialog"></a>效能管理員對話方塊

![效能 [管理員] 對話方塊](media/performance-manager.png)

同步已載入的任何使用者工作階段中的任何套件的所有擴充功能會出現在**已被取代的 Api**  索引標籤。

* 使用者可以按一下**此問題的詳細資訊**收集已被取代的 Api 的詳細資訊。
* 使用者可以將其延伸模組廠商連絡移轉進度。

延伸模組作者可以找到移轉指示封裝在非同步 autoload[移轉至 AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)。

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>指定同步 autoload 設定使用群組原則

啟動 Visual Studio 2019 Update 1 中，根據預設，Visual Studio 安裝區塊同步 autoload。 當您啟用群組原則時，您可以設定以允許同步 autoload 個別的電腦上的 Visual Studio。 若要這樣做，請在下列機碼上設定以登錄為基礎的原則：

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

項目 =**允許**

值 = (DWORD)
* **0**同步 autoload 不允許
* **1**允許同步 autoload

如需 Visual Studio 2019 Update 1 中的同步 autoload 設定的詳細資訊，請參閱[同步 Autoload 行為](https://aka.ms/AA52xzw)頁面。
