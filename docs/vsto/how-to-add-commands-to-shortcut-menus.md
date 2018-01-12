---
title: "如何： 將命令加入至快顯功能表 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 361809dd94ae1419c5c6d2d06470d4d8d025cecf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>如何：將命令加入到捷徑功能表
  本主題示範如何使用 VSTO 增益集將命令加入 Office 應用程式的捷徑功能表中。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>將命令加入 Office 的捷徑功能表  
  
1.  將 **功能區 XML** 項目加入文件層級或 VSTO 增益集專案。 如需詳細資訊，請參閱 [如何：開始自定義功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。 In  
  
2.  在方案總管中，選取 **ThisAddin.cs** 或 **ThisAddin.vb**。  
  
3.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     **ThisAddin** 類別隨即在程式碼編輯器中開啟。  
  
4.  將下列程式碼加入 **ThisAddin** 類別中。 此程式碼會覆寫 CreateRibbonExtensibilityObject 方法，而此功能區 XML 類別傳回 Office 應用程式。  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  在方案總管 中選取功能區 XML 檔案。 根據預設，功能區 XML 檔名為 Ribbon1.xml。  
  
6.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     功能區 XML 檔案隨即在程式碼編輯器中開啟。  
  
7.  在程式碼編輯器中，加入描述捷徑功能表以及您想要加入捷徑功能表之控制項的 XML。  
  
     下列範例會將按鈕、功能表和圖庫控制項加入 Word 文件的捷徑功能表。 這個捷徑功能表的控制項 ID 是 ContextMenuText。 如需完整清單的 Office 2010 捷徑控制項 ID，請參閱[Office 2010 說明檔： Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  在方案總管 中，選擇 **MyRibbon.cs** 或 **MyRibbon.vb**。  
  
9. 針對您想要處理的每個控制項，將回呼方法加入 `Ribbon1` 類別。  
  
     下列回呼方法會處理 [My Button]  按鈕。 此程式碼會在使用中文件的目前游標位置加入字串。  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>請參閱  
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [逐步解說： 建立書籤的捷徑功能表](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [自訂 Office 2010 中的內容功能表](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  