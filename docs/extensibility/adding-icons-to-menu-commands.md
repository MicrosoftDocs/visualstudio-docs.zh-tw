---
title: 將圖示加入至功能表命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8591c55a176493ace23df2de61ba26d58a3155e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098388"
---
# <a name="adding-icons-to-menu-commands"></a>將圖示加入至功能表命令
命令可以出現在功能表和工具列。 在工具列上很常見的只是圖示 （為了節省空間） 時功能表上顯示命令通常會顯示圖示和文字的命令。  
  
 圖示是 16 像素寬 x 16 像素高，而且可以是 8 位元色彩深度 （256 色） 或 32 位元色彩深度 （全彩）。 偏好採用的 32 位元色彩圖示。 雖然允許多個點陣圖圖示通常會排列在單一的點陣圖，單一水平列。 .Vsct 檔，以及個別點陣圖中可用的圖示中宣告這個點陣圖。 請參閱參考[點陣圖項目](../extensibility/bitmaps-element.md)如需詳細資訊。  
  
## <a name="adding-an-icon-to-a-command"></a>將圖示加入至命令  
 下列程序假設您有現有的 VSPackage 專案中的功能表命令。 若要了解如何執行這項操作，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
1.  建立點陣圖的 32 位元色彩深度。 圖示永遠是 16 x 16，所以此點陣圖必須是 16 像素高和 16 個像素寬的倍數。  
  
     每個圖示會放在相鄰點陣圖中的單一資料列。 您可以使用 alpha 色板，表示透明度中每個圖示的位置。  
  
     如果您使用 8 位元色彩深度，使用洋紅色、 `RGB(255,0,255)`，做為透明。 不過，32 位元色彩圖示是慣用的。  
  
2.  將圖示檔複製到您的 VSPackage 專案中的 [資源] 目錄。 在 [方案總管] 中，將圖示新增至專案。 （選取資源，並在內容功能表上按一下 加入 和 現有項目，並選取圖示檔。）  
  
3.  在編輯器中開啟.vsct 檔。  
  
4.  新增`GuidSymbol`元素名稱為**testIcon**。 建立 GUID (**工具 / 建立 GUID**，然後選取**登錄格式**然後按一下 複製) 並將它貼入`value`屬性。 結果看起來應該像這樣：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  新增`<IDSymbol>`圖示。 `name`屬性是圖示的識別碼，而`value`指出在區域上的位置，如果有的話。 如果有一個圖示，會加 1。 結果看起來應該像這樣：  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  建立`<Bitmap>`中`<Bitmaps>`來代表包含圖示的點陣圖.vsct 檔的區段。  
  
    -   設定`guid`值的名稱`<GuidSymbol>`您在上一個步驟中建立的項目。  
  
    -   設定`href`點陣圖檔案的相對路徑的值 (在此情況下**資源\\< 圖示檔檔名\>**。  
  
    -   設定`usedList`IDSymbol 您稍早建立的值。 這個屬性會指定以逗號分隔的清單圖示，即可在 VSPackage 中使用。 排除的表單編譯是不在清單上的圖示。  
  
         點陣圖區塊應該看起來像這樣：  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  在現有`<Button>`項目，設定`Icon`GUIDSymbol 和 IDSymbol 值您稍早建立的項目。 按鈕項目使用這些值的範例如下：  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  測試您的圖示。 建置此專案並開始偵錯。 在實驗性執行個體中，找到的命令。 它應該會顯示圖示您加入。  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)