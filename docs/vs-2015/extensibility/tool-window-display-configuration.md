---
title: 工具視窗中顯示組態 |Microsoft Docs
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
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ff1e5b95b684c347ee1885d5dfddeb5eebb5a82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498457"
---
# <a name="tool-window-display-configuration"></a>工具視窗中顯示組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[工具視窗中顯示組態](https://docs.microsoft.com/visualstudio/extensibility/tool-window-display-configuration)。  
  
當向 VSPackage 註冊工具視窗、 預設位置、 大小、 停駐樣式，以及其他的可見性資訊，被指定選擇性的值。 如需有關工具視窗中註冊的詳細資訊，請參閱[工具 Windows 登錄中](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>視窗顯示資訊  
 工具視窗的基本顯示組態儲存在最多六個選擇性的值：  
  
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
|名稱|REG_SZ|「 在此輸入簡短名稱 」|描述 [工具] 視窗的簡短名稱。 僅用於在登錄中的參考。|  
|浮動|REG_SZ|"X1，Y1，X2，Y2"|四個以逗號分隔值。 X1，Y1 是工具視窗的左上角的座標。 X2，Y2 是右下角的座標。 所有值都會以螢幕座標表示。|  
|樣式|REG_SZ|「 MDI"<br /><br /> 「 浮動 」<br /><br /> 「 連結 」<br /><br /> 「 索引 」<br /><br /> 「 AlwaysFloat"|指定初始的關鍵字會顯示工具視窗的狀態。<br /><br /> 「 MDI"= 停駐在一起的 MDI 視窗。<br /><br /> 「 浮動 」 = 浮點數。<br /><br /> 「 連結 」 = 與另一個視窗 （在視窗項目中指定） 連結。<br /><br /> 「 索引標籤式"= 結合另一個工具視窗。<br /><br /> 「 AlwaysFloat"= 無法停駐。<br /><br /> 如需詳細資訊，請參閱下方的註解區段。|  
|視窗|REG_SZ|*\<GUID &GT;*|視窗的 [工具] 視窗可以連結或索引標籤式的 GUID。 GUID 可能屬於其中一個您自己的視窗或其中一個在 windows [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE。|  
|方向|REG_SZ|"Left"<br /><br /> 權利 」<br /><br /> "Top"<br /><br /> 「 下 」|請參閱下方的註解區段。|  
|DontForceCreate|REG_DWORD|0 或 1|當此項目存在，且其值不是零時，是視窗載入，但不是會立即顯示。|  
  
### <a name="comments"></a>註解  
 方向的項目定義按兩下標題列時的工具視窗停駐的位置。 這個位置是相對於視窗項目中指定的視窗。 如果樣式項目設定為 「 連結 」，方向的項目可以是"Left"、"Right"、"Top"或 「 底部 」。 如果樣式項目是 「 索引標籤式 」、 方向的項目可以 「 保留 」 或 「 右 」，並指定 [] 索引標籤加入的位置。 如果樣式項目是 「 浮動 」，第一次浮動工具視窗。 按兩下標題列時，將套用的方向和視窗的項目，和視窗使用 「 索引標籤式 」 樣式。 如果"AlwaysFloat 」 的樣式項目，不能停駐工具視窗。 如果"MDI"的樣式項目，工具視窗會連結到 MDI 區域中，並會忽略視窗項目。  
  
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
  
## <a name="tool-window-visibility"></a>工具視窗可見性  
 選擇性的可見性子機碼中的值可決定工具視窗的可見性設定。 值的名稱會用來儲存需要視窗的可見性的命令的 Guid。 如果命令執行時，IDE 會保證是建立工具視窗，並顯示。  
  
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
|(預設值)|REG_SZ|無|將保留空白。|  
|*\<GUID &GT;*|REG_DWORD 或 REG_SZ|0 或描述性字串。|選擇性。 項目名稱必須是需要可見性命令的 GUID。 值只會保留資訊的字串。 值通常是`reg_dword`設為 0。|  
  
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

