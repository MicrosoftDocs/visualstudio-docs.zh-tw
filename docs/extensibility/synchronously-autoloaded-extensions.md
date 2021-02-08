---
title: 非同步自動載入延伸模組
description: 瞭解從 Visual Studio 2019 開始的預設行為，這會封鎖從任何擴充功能同步自動載入封裝。
ms.custom: SEO-VS-2020
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 460227b1eb5a1e12ca698f649700586b53bc7254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839331"
---
# <a name="synchronously-autoloaded-extensions"></a>非同步自動載入延伸模組

同步自動載入延伸對 Visual Studio 的效能有負面影響，而且應該轉換成使用非同步自動載入。 根據預設，Visual Studio 2019 會封鎖從任何擴充功能同步自動載入套件，並通知使用者。

![延伸模組相容性警告](media/extension-compatibility-warning-16-1.png.png)

您可以：

- 按一下 [ **允許同步自動載入** 允許自動載入的延伸模組]。 若要在 Visual Studio 選項中變更此設定，請按一下 [環境]，然後按一下 [擴充功能]，再選取 [允許延伸的同步自動載入] 核取方塊。 

- 按一下 [ **管理效能** ] 開啟 [ [效能管理員] 對話方塊](#performance-manager-dialog) ，以顯示延伸模組和工具視窗的效能問題。

- 按一下 [ **不要針對目前的擴充功能顯示此訊息** ] 來解除通知，並防止未來現有已安裝延伸模組的通知。 如果您加入同步 autoloads 的新延伸模組，此通知會再次顯示。 您將會繼續取得有關其他 Visual Studio 功能的通知。

## <a name="performance-manager-dialog"></a>效能管理員對話方塊

![效能管理員對話方塊](media/performance-manager.png)

在任何使用者會話中同步載入任何套件的所有延伸模組都會出現在 [已 **淘汰的 api** ] 索引標籤中。

* 按一下 **此問題的詳細資訊** ，以收集已淘汰 api 的詳細資訊。
* 請洽詢擴充廠商以取得遷移進度。

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>使用群組原則指定同步自動載入設定

系統管理員可以啟用群組原則以允許同步自動載入。 若要這樣做，請在下列機碼上設定以登錄為基礎的原則：

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

專案 = **允許**

Value = (DWORD)
* **0** 是不允許的同步自動載入
* **1** 是允許的同步自動載入

## <a name="extension-authors"></a>延伸模組作者
延伸模組作者可以找到在 [遷移至 AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)時，將封裝遷移至非同步自動載入的指示。

## <a name="see-also"></a>另請參閱
如需 Visual Studio 2019 中同步自動載入設定的詳細資訊，請參閱 [同步自動載入行為](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) 頁面。
