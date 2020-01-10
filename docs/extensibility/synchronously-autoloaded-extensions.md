---
title: 非同步自動載入延伸模組
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa26585ff4cca909a7fb7c955b351b8860436b4
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406625"
---
# <a name="synchronously-autoloaded-extensions"></a>非同步自動載入延伸模組

同步自動載入延伸模組對 Visual Studio 的效能會有負面影響，而且應該改為使用非同步 autoload。 根據預設，Visual Studio 2019 會封鎖從任何延伸模組同步自動載入封裝，並通知使用者。

![延伸模組相容性警告](media/extension-compatibility-warning-16-1.png.png)

您可以：

- 按一下 [**允許同步 autoload** ] 以允許 autoload 的延伸模組。 若要在 Visual Studio 選項中變更此設定，請按一下 [環境]，然後按一下 [擴充功能]，再選取 [允許同步 autoload 擴充功能] 核取方塊。 

- 按一下 [**管理效能**] 以開啟 [[效能管理員] 對話方塊](#performance-manager-dialog)，其中顯示擴充功能和工具視窗的效能問題。

- 按一下 [**不要針對目前的延伸顯示此訊息**] 來解除通知，並防止未來現有的已安裝延伸模組通知。 如果您加入以同步方式 autoloads 的新延伸模組，則會再次顯示此通知。 您會繼續收到有關其他 Visual Studio 功能的通知。

## <a name="performance-manager-dialog"></a>[效能管理員] 對話方塊

![[效能管理員] 對話方塊](media/performance-manager.png)

同步載入任何使用者會話中任何套件的所有延伸模組，都會出現在 [已**淘汰的 api** ] 索引標籤中。

* 按一下**此問題的詳細資訊**，以收集已淘汰之 api 的詳細資訊。
* 請洽詢其擴充廠商以進行遷移進度。

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>使用群組原則指定同步 autoload 設定

系統管理員可以啟用群組原則來允許同步 autoload。 若要這樣做，請在下列機碼上設定以登錄為基礎的原則：

**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entry =**允許**

值 = (DWORD)
* **0**是不允許的同步 autoload
* **1**是允許同步 autoload

## <a name="extension-authors"></a>延伸模組作者
延伸模組作者可以在[遷移至 AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)找到將封裝遷移至非同步 autoload 的指示。

## <a name="see-also"></a>請參閱
如需 Visual Studio 2019 中同步 autoload 設定的詳細資訊，請參閱[同步 Autoload 行為](https://aka.ms/AA52xzw)頁面。
