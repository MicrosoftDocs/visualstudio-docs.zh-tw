---
title: 將圖示加入至功能表命令 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 051fc6b33a04870f0d21e14ecbe0adc8fcd525be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489661"
---
# <a name="adding-icons-to-menu-commands"></a>將圖示新增至功能表命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[加入至功能表命令的圖示](https://docs.microsoft.com/visualstudio/extensibility/adding-icons-to-menu-commands)。  
  
命令可以出現在功能表和工具列。 在工具列上很常見的只是圖示 （以節省空間） 時在功能表上顯示命令通常會出現圖示和文字的命令。  
  
 圖示是 16 像素寬 x 16 像素高，而且可以是 8 位元色彩深度 （256 色） 或 32 位元色彩深度 （全彩）。 32 位元色彩圖示較好。 圖示通常會排列在單一的水平資料列，在單一點陣圖，雖然允許多個點陣圖。 這個點陣圖被宣告以及個別的圖示和點陣圖中，您可以使用.vsct 檔案中。 請參閱參考[Bitmaps 元素](../extensibility/bitmaps-element.md)如需詳細資訊。  
  
## <a name="adding-an-icon-to-a-command"></a>將圖示新增至命令  
 下列程序假設您有現有的功能表命令的 VSPackage 專案。 若要了解如何執行這項操作，請參閱[建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
1.  建立與色彩深度為 32 位元的點陣圖。 圖示永遠是 16 x 16，因此此點陣圖必須是 16 像素高和 16 像素寬的倍數。  
  
     每個圖示都放在彼此相鄰的點陣圖中的單一資料列。 您可以使用 alpha 色頻來表示透明度中每個圖示的位置。  
  
     如果您使用的 8 位元色彩深度時，使用洋紅、 `RGB(255,0,255)`，做為透明。 不過，32 位元色彩圖示為慣用。  
  
2.  將圖示檔複製到 VSPackage 專案中的 [資源] 目錄中。 在 [方案總管] 中，將圖示新增至專案。 （選取的資源，並在操作功能表上按一下 加入 和 現有項目，然後選取圖示檔。）  
  
3.  在編輯器中開啟.vsct 檔。  
  
4.  新增`GuidSymbol`項目名稱取代**testIcon**。 建立 GUID (**工具 / 建立 GUID**，然後選取**登錄格式**按一下 複製) 將它貼至`value`屬性。 結果應該如下所示：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  新增`<IDSymbol>`圖示。 `name`屬性是圖示的識別碼和`value`表示功能表列上的位置，如果有的話。 如果有一個圖示，將 1 加入。 結果應該如下所示：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  建立`<Bitmap>`在`<Bitmaps>`來代表包含圖示的點陣圖.vsct 檔的區段。  
  
    -   設定`guid`值的名稱`<GuidSymbol>`您在上一個步驟中建立的項目。  
  
    -   設定`href`點陣圖檔的相對路徑的值 (在此情況下**資源\\< 圖示檔檔名\>**。  
  
    -   設定`usedList`IDSymbol 您稍早建立的值。 這個屬性會指定要用於 VSPackage 的圖示以逗號分隔清單。 排除的表單編譯是不在清單上的圖示。  
  
         點陣圖區塊看起來應該像這樣：  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  在現有`<Button>`項目，設定`Icon`GUIDSymbol 和 IDSymbol 值您稍早建立的項目。 以下是範例的按鈕項目使用這些值：  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  測試您的圖示。 建置此專案並開始偵錯。 在實驗執行個體中，找到的命令。 它應該會顯示圖示您加入。  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)

