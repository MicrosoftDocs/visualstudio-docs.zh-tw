---
title: "按鈕項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd630a2fed94604cb91dc3af7e46f96269f75ad0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="button-element"></a>Button 項目
定義使用者可以與之互動的項目。 按鈕可以屬於不同類型： 按鈕、 MenuButton 和 SplitDropDown。  
  
## <a name="syntax"></a>語法  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|Guid|必要項。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要項。 GUID/識別碼命令識別項的識別碼。|  
|priority|選擇項。 數值，指定的優先權。|  
|類型|選擇項。 列舉的值，指定按鈕類型。<br /><br /> 如果沒有指定，會使用按鈕。<br /><br /> 按鈕<br /> 標準命令，會出現在工具列上 （通常為圖示的按鈕），功能表和操作功能表。<br /><br /> MenuButton<br /> 功能表項目不會執行命令，但會產生另一個功能表。<br /><br /> SplitDropDown<br /> 控制項，例如 Microsoft Word 中的 [標準] 工具列上的復原與取消復原按鈕。|  
|條件|選擇項。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[Parent 元素](../extensibility/parent-element.md)|選擇項。 按鈕的父項目。|  
|[Icon 元素](../extensibility/icon-element.md)|選擇項。 與按鈕相關聯的圖示。|  
|[Command Flag 元素](../extensibility/command-flag-element.md)|必要項。 CommandFlag 按鈕的有效值，如下所示。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -文字變更<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings 元素](../extensibility/strings-element.md)|必要項。 子系[ButtonText 元素](../extensibility/buttontext-element.md)必須定義。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組按鈕項目。|  
  
## <a name="example"></a>範例  
 下列範例會定義在.vsct 檔案中的按鈕。  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)