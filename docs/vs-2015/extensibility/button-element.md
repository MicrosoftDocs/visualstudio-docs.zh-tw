---
title: 按鈕項目 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58f63968ed02f49b0ccfa4dda24f684fed339bc4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939611"
---
# <a name="button-element"></a>Button 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義使用者可以互動的項目。 按鈕可以是不同類型：按鈕、 MenuButton 和 SplitDropDown。  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要項。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要項。 GUID/識別碼的命令識別項的識別碼。|  
|priority|選擇性。 數值，指定的優先權。|  
|類型|選擇性。 列舉的值，指定的按鈕類型。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> 按鈕<br /> 會出現在工具列 （通常為圖示的按鈕），功能表和快顯功能表標準命令。<br /><br /> MenuButton<br /> 功能表項目不會執行命令，但會產生另一個功能表。<br /><br /> SplitDropDown<br /> 控制項，例如 Microsoft Word 中的 [標準] 工具列上的 [復原與取消復原] 按鈕。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Parent 元素](../extensibility/parent-element.md)|選擇性。 按鈕的父項目。|  
|[Icon 元素](../extensibility/icon-element.md)|選擇性。 與按鈕關聯的圖示。|  
|[Command Flag 元素](../extensibility/command-flag-element.md)|必要項。 CommandFlag 按鈕有效值，如下所示。<br /><br /> - AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> - IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -Pict<br /><br /> - PostExec<br /><br /> -ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -文字變更<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings 元素](../extensibility/strings-element.md)|必要項。 子系[ButtonText 元素](../extensibility/buttontext-element.md)必須定義。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|分組按鈕項目。|  
  
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
