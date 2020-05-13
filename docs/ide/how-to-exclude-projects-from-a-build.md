---
title: 如何：從組建中排除專案
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114811"
---
# <a name="how-to-exclude-projects-from-a-build"></a>如何：從組建中排除專案

您可以建置方案，而不建置它所包含的所有專案。 例如，您可能會排除會中斷組建的專案。 然後您可以在調查和處理這些問題之後才建置專案。

您可以利用下列方式排除專案：

- 從作用中的方案組態暫時將其移除。

- 建立不包含專案的方案組態。

如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>從作用中的方案組態暫時將專案移除

1. 在功能表列上，選擇 **"生成** > **組態管理員**"。

2. 在 [專案內容]**** 資料表中，找出您想要從組建排除的專案。

3. 在專案的 [組建]**** 資料行中，清除核取方塊。

4. 選擇 [關閉]**** 按鈕，然後重新建置方案。

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>建立排除專案的方案組態

1. 在功能表列上，選擇 **"生成** > **組態管理員**"。

2. 在 **"活動解決方案配置**"清單中，選擇**\<"新建>**"。

3. 在 [名稱]**** 方塊中，輸入方案組態的名稱。

4. 在 [複製設定來源]**** 清單中，選擇您要以其為新組態根據的方案組態 (例如，偵錯****)，然後選擇 [確定]**** 按鈕。

5. 在 [組態管理員]**** 對話方塊中，清除 [建置]**** 資料行中您想要排除之專案的核取方塊，然後選擇 [關閉]**** 按鈕。

6. 在 [標準]**** 工具列上，確認新的方案組態是 [方案組態]**** 方塊中的使用中組態。

7. 在功能表列上，選擇 **"生成** > **重建解決方案**"。

## <a name="skipped-projects"></a>跳過的專案

可以在生成期間跳過專案，因為它們不是最新的，或者因為它們被排除在配置之外。 Visual Studio 使用 MSBuild 構建專案。 MSBuild 僅在輸出早于輸入（由檔時間戳記確定）時生成目標。 要強制重建，請使用命令**生成** > **重建解決方案**。

在 **"輸出**"視窗的 **"生成**"窗格中，Visual Studio 報告最新的專案數、成功生成的專案數、失敗的編號以及跳過的專案數。 跳過的計數不包括未生成的專案，因為它們是最新的。 當專案從活動配置中排除時，它們在生成期間被跳過。 在生成輸出中，您將看到一條消息，指示專案已跳過：

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

`Debug x86`要找出跳過專案的原因，請注意活動配置（在前面的示例中），然後選擇**生成** > **組態管理員**。 您可以查看或更改每個配置跳過哪些專案，如本文所述。

## <a name="see-also"></a>另請參閱

- [瞭解組建組態](../ide/understanding-build-configurations.md)
- [如何：創建和編輯配置](../ide/how-to-create-and-edit-configurations.md)
- [如何：同時構建多個配置](../ide/how-to-build-multiple-configurations-simultaneously.md)
