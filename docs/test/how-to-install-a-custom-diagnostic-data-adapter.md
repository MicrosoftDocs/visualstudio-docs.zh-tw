---
title: 如何：在 Visual Studio 中安裝自訂的診斷資料配接器
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24ce9f954164cd8d243edfab4387f6b174c0648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>如何：安裝自訂的診斷資料配接器

如果您已建立自訂診斷資料配接器，或獲得可用的自訂診斷資料配接器，您可以將診斷資料配接器組件的組件檔複製至本機電腦的正確目錄中，以安裝該組件。

 若要針對環境中的某個角色使用自訂診斷資料配接器，您必須在所有執行測試代理程式 (可用於此角色) 的電腦上安裝該診斷資料配接器。

 使用下列程序，在適當的位置中安裝您的自訂診斷配接器。 在安裝診斷資料配接器的電腦上，您必須具有其系統管理權限。

## <a name="installing-a-custom-diagnostic-data-adapter"></a>安裝自訂的診斷資料配接器

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>安裝自訂的診斷資料配接器

1.  若要在用戶端電腦上或代理程式電腦上執行測試時，使用診斷配接器，請根據安裝路徑，將組建目錄中的所有檔案複製至目標電腦上下列目錄：

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     要複製的檔案為：

    -   診斷資料配接器組件 (.dll) (必要項)。

    -   配接器的偵錯資料檔案 (.pdb) (選擇性)。

    -   如果具有預設組態設定，則為配接器的組態檔 (`<diagnostic data adapter name>.dll.config`) (選擇性)。

    -   如果已建立組態編輯器組建來編輯配接器的組態設定，則為該組態編輯器組件 (選擇性)。 此項僅適用於用戶端電腦。 代理程式電腦不使用編輯器。

    > [!NOTE]
    > 雖然可以在相同專案裝建立診斷資料配接器和組態編輯器，並可建置到相同的組件，但您也可以選擇使用不同的專案，並對這些專案建立不同的組件。

     如需如何設定測試設定以便在執行測試時使用環境的詳細資訊，請參閱[在手動測試中收集診斷資料 (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)。

2.  若要選取診斷資料配接器以進行測試，您必須先從 Microsoft Test Manager 或 Visual Studio 選取現有的測試設定或建立新的設定，然後在所選測試設定的 [資料和診斷] 索引標籤上，選取診斷資料配接器。

3.  如果您已建立並安裝診斷資料配接器組態編輯器，若要在測試設定中設定診斷資料配接器，請選擇配接器旁的 [設定] 並進行任何變更。 然後選擇 [儲存]。 如需如何為診斷資料收集器建立組態編輯器的詳細資訊，請參閱[如何：為您的診斷資料配接器建立資料的自訂編輯器](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)。

4.  如果您從 Microsoft Test Manager 執行測試，您可以在執行測試前將這些測試設定指派給測試計劃，或使用 [以選項執行] 命令來指派測試設定和覆寫測試設定。 如需測試設定的詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

     如果您要從 Visual Studio 執行測試，則必須將這些測試設定設為作用中。 如需測試設定的詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

5.  使用已選取該診斷資料配接器的測試設定來執行您的測試。

## <a name="see-also"></a>另請參閱

- [如何：建立診斷資料配接器](../test/how-to-create-a-diagnostic-data-adapter.md)
- [如何：為您的診斷資料配接器建立資料的自訂編輯器](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [建立診斷資料配接器的範例專案](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [建立診斷資料配接器以收集自訂資料或影響測試電腦](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)