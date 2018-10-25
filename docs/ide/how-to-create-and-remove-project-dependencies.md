---
title: 如何：建立和移除專案相依性
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7075f21f7927a87968dd573863402a71a40c3c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856011"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>如何：建立和移除專案相依性

在建置包含多個專案的方案時，您可能需要先建置特定專案，以產生其他專案使用的程式碼。 當某個專案使用其他專案所產生的可執行程式碼時，產生程式碼的專案和使用程式碼的專案之間即具有專案相依性。 您可以在 [專案相依性] 對話方塊中定義這類相依性關聯。

## <a name="to-assign-dependencies-to-projects"></a>指派專案相依性

1. 在方案總管中選取專案。

2. 在 [專案] 功能表上，選擇 [專案相依性]。

    [專案相依性] 對話方塊隨即開啟。

   > [!NOTE]
   > [專案相依性] 選項只適用於具有多個專案的方案。

3. 在 [相依性] 索引標籤上，選取 [專案] 下拉式功能表中的專案。

4. 如果任何其他專案必須在此專案之前建置，請在 [相依於] 欄位中，選取該專案的核取方塊。

   您的方案必須包含一個以上的專案，才可以建立專案相依性。

## <a name="to-remove-dependencies-from-projects"></a>若要從專案移除相依性

1.  在方案總管中選取專案。

2.  在 [專案] 功能表上，選擇 [專案相依性]。

     [專案相依性] 對話方塊隨即開啟。

    > [!NOTE]
    > [專案相依性] 選項只適用於具有多個專案的方案。

3.  在 [相依性] 索引標籤上，選取 [專案] 下拉式功能表中的專案。

4.  如果任何其他專案不再與此專案具有相依性，請在 [相依於] 欄位中，清除這些專案旁的核取方塊。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [了解建置組態](../ide/understanding-build-configurations.md)
- [管理專案及解決方案屬性](managing-project-and-solution-properties.md)