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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114811"
---
# <a name="how-to-exclude-projects-from-a-build"></a>如何：從組建中排除專案

您可以建置方案，而不建置它所包含的所有專案。 例如，您可能會排除會中斷組建的專案。 然後您可以在調查和處理這些問題之後才建置專案。

您可以利用下列方式排除專案：

- 從作用中的方案組態暫時將其移除。

- 建立不包含專案的方案組態。

如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>從作用中的方案組態暫時將專案移除

1. 在功能表列上，選擇 [建置] > [組態管理員]。

2. 在 [專案內容] 資料表中，找出您想要從組建排除的專案。

3. 在專案的 [組建] 資料行中，清除核取方塊。

4. 選擇 [關閉] 按鈕，然後重新建置方案。

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>建立排除專案的方案組態

1. 在功能表列上，選擇 [建置] > [組態管理員]。

2. 在 [使用中的方案組態] 清單中，選擇 [\<新增>]。

3. 在 [名稱] 方塊中，輸入方案組態的名稱。

4. 在 [複製設定來源] 清單中，選擇您要以其為新組態根據的方案組態 (例如，偵錯)，然後選擇 [確定] 按鈕。

5. 在 [組態管理員] 對話方塊中，清除 [建置] 資料行中您想要排除之專案的核取方塊，然後選擇 [關閉] 按鈕。

6. 在 [標準] 工具列上，確認新的方案組態是 [方案組態] 方塊中的使用中組態。

7. 在功能表列上，依序選擇 [建置] > [重建方案]。

## <a name="skipped-projects"></a>略過的專案

專案可以在組建期間略過，因為它們不是最新狀態，或是因為它們已從設定中排除。 Visual Studio 使用 MSBuild 來建立您的專案。 如果輸出比輸入還舊，MSBuild 只會建立目標，如同檔案時間戳記所決定。 若要強制重建，請使用命令**組建** > **重建解決方案**。

在 [**輸出**] 視窗的 [**建立**] 窗格中，Visual Studio 報告最新的專案數、成功建立的數目、失敗的數目，以及略過的數位。 略過的計數不包括因為已是最新狀態而未建立的專案。 當專案從作用中設定排除時，會在組建期間略過它們。 在組建輸出中，您會看到一則訊息，指出已略過該專案：

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

若要找出專案略過的原因，請注意作用中的設定（上一個範例中的`Debug x86`），然後選擇 [**組建** > ] **Configuration Manager**。 如本文所述，您可以查看或變更每個設定略過的專案。

## <a name="see-also"></a>請參閱

- [了解建置組態](../ide/understanding-build-configurations.md)
- [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)
- [如何：同時建置多個組態](../ide/how-to-build-multiple-configurations-simultaneously.md)
