---
title: 工具視窗顯示設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186401"
---
# <a name="tool-window-display-configuration"></a>工具視窗顯示組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當 VSPackage 註冊工具視窗時，會在選擇性的值中指定預設的位置、大小、停駐樣式和其他可見度資訊。 如需工具視窗註冊的詳細資訊，請參閱[登錄中的工具](../extensibility/tool-windows-in-the-registry.md)視窗  
  
## <a name="window-display-information"></a>視窗顯示資訊  
 工具視窗的基本顯示設定最多可儲存六個選擇性值：  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|「簡短名稱在此|描述工具視窗的簡短名稱。 僅用於登錄中的參考。|  
|Float|REG_SZ|"X1、Y1、X2、Y2"|四個逗號分隔值。 X1，Y1 是工具視窗左上角的座標。 X2，Y2 是右下角的座標。 所有值都是以螢幕座標表示。|  
|樣式|REG_SZ|MDI<br /><br /> 浮點<br /><br /> 起來<br /><br /> 製表<br /><br /> "AlwaysFloat"|關鍵字，指定工具視窗的初始顯示狀態。<br /><br /> "MDI" = 停駐在 MDI 視窗。<br /><br /> "Float" = 浮動。<br /><br /> 「連結」 = 與視窗專案) 中指定的另一個視窗 (連結。<br /><br /> 「索引標籤式」 = 與另一個工具視窗結合。<br /><br /> "AlwaysFloat" = 無法停駐。<br /><br /> 如需詳細資訊，請參閱下面的「批註」一節。|  
|時間範圍|REG_SZ|*\<GUID>*|可以連結工具視窗或索引標籤之視窗的 GUID。 GUID 可能屬於您自己的其中一個視窗或 IDE 中的其中一個視窗 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。|  
|方向|REG_SZ|方<br /><br /> 右下<br /><br /> 自頂向下<br /><br /> 底部|請參閱下面的「批註」一節。|  
|DontForceCreate|REG_DWORD|0 或 1|當這個專案存在且其值不是零時，就會載入該視窗，但不會立即顯示。|  
  
### <a name="comments"></a>註解  
 [方向] 專案會定義當按兩下其標題列時，工具視窗的停駐位置。 位置是相對於視窗專案中指定的視窗。 如果樣式專案設定為 [已連結]，則方向專案可以是「左」、「右側」、「頂端」或「底部」。 如果樣式專案是「索引標籤式」，則方向專案可以是「左」或「右」，並指定要加入索引標籤的位置。 如果樣式專案為 "Float"，則工具視窗會先浮動。 按兩下標題列時，會套用 [方向] 和 [視窗] 專案，而視窗則會使用「索引標籤式」樣式。 如果樣式專案為 "AlwaysFloat"，則無法停駐工具視窗。 如果樣式專案為 "MDI"，則工具視窗會連結至 MDI 區域，而且會忽略視窗專案。  
  
### <a name="example"></a>範例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>工具視窗可見度  
 選擇性可見度子機碼中的值會決定工具視窗的可見度設定。 值的名稱是用來儲存需要視窗可見度的命令 Guid。 如果命令已執行，IDE 會保證工具視窗已建立並顯示。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|名稱|類型|資料|描述|  
|----------|----------|----------|-----------------|  
|(預設值)|REG_SZ|無|保留空白。|  
|*\<GUID>*|REG_DWORD 或 REG_SZ|0或描述性字串。|選擇性。 專案的名稱必須是需要可見度的命令 GUID。 值只會保存有資訊的字串。 一般而言，值是 `reg_dword` 設定為0。|  
  
### <a name="example"></a>範例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 基本資訊](../misc/vspackage-essentials.md)
