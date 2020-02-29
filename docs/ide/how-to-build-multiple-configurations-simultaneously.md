---
title: 如何：同時建置多個組態
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cd217a08f62b4919af6d72017176c110cf5e5a
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904083"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>如何：同時建置多個組態

您可以使用 [批次建置] 對話方塊，同時建置具有多個甚至所有組建組態的多數類型專案。 不過，您無法同時在多個組建組態中組建下列類型的專案：

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式是使用 JavaScript 針對 Windows 建置。

2. 所有 Visual Basic 專案。

如果方案包含這兩個專案類型的任何專案，則該方案無法使用**批次組建**。 在此情況下，命令不會出現在 [**建立**] 功能表上。

   如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

## <a name="to-build-a-project-in-multiple-build-configurations"></a>在多個組建組態中建置專案

1. 在功能表列上，選擇 [建置] > [批次建置]。 或者，按**Ctrl**+**Q**開啟 [搜尋] 方塊，然後搜尋 `Batch Build`。

2. 在 [建置] 資料行中，選取您要用來建置專案之組態的核取方塊。

    > [!TIP]
    > 若要編輯或建立解決方案的組建組態，請選擇功能表列上的 [建置] > [組態管理員] 以開啟 [組態管理員] 對話方塊。 在您編輯方案的組建組態之後，請在 [批次建置] 對話方塊中選擇 [重建] 按鈕，來更新方案中專案的所有組建組態。

3. 選擇 [建置] 或 [重建] 按鈕，以使用您指定的組態來建置專案。

## <a name="see-also"></a>另請參閱

- [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)
- [了解建置組態](../ide/understanding-build-configurations.md)
- [平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)