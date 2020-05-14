---
title: 非同步自動載入延伸模組
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699376"
---
# <a name="synchronously-autoloaded-extensions"></a>非同步自動載入延伸模組

同步自動載入擴展對 Visual Studio 的性能產生負面影響,應轉換為使用非同步自動載入。 默認情況下,Visual Studio 2019 阻止任何擴展同步自動載入包並通知使用者。

![延伸相容性警告](media/extension-compatibility-warning-16-1.png.png)

您可以：

- 按下「**允許同步自動載入**以允許自動載入擴展」。 要在 Visual Studio 選項中更改此設置,請單擊「環境」,然後按一下「擴展」,然後選擇複選框「允許擴展的同步自動載入」。 

- 點選「**管理效能**」 以開啟顯示擴充與工具視窗[的效能問題的效能管理員對話框](#performance-manager-dialog)。

- 按下「**不要顯示目前擴展此訊息**」 以關閉通知並防止將來通知來自現有已安裝的擴展。 如果添加同步自動載入的新擴展,將再次顯示此通知。 您將繼續收到有關其他視覺工作室功能的通知。

## <a name="performance-manager-dialog"></a>效能管理員對話框

![效能管理員對話框](media/performance-manager.png)

在任何使用者作業階段中同步載入任何包的所有擴展都將顯示在 **「已棄用 API」** 選項卡中。

* 按一下有關**此問題的詳細資訊**「以收集有關已棄用 API 的詳細資訊。
* 有關遷移進度,請與其擴展供應商聯繫。

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>使用群組政策指定同步自動載入設定

管理員可以啟用組策略以允許同步自動載入。 若要這樣做，請在下列機碼上設定以登錄為基礎的原則：

**HKEY_LOCAL_MACHINE_軟體_策略\微軟_VisualStudio_同步自動載入**

項目 =**允許**

Value = (DWORD)
* **0**是不允許同步自動載入
* **1**是允許同步自動載入

## <a name="extension-authors"></a>擴充作者
擴展作者可以在[遷移到非同步包](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)時找到有關將包遷移到非同步自動載入的說明。

## <a name="see-also"></a>另請參閱
有關 Visual Studio 2019 中的同步自動載入設定的詳細資訊,請參閱[同步自動載入行為](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)頁面。
