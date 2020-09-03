---
title: Button 元素 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184544"
---
# <a name="button-element"></a>Button 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義使用者可以與之互動的元素。 按鈕可以是不同的類型： Button、MenuButton 和 SplitDropDown。  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼命令識別碼的識別碼。|  
|priority|選擇性。 指定優先權的數位值。|  
|type|選擇性。 指定按鈕種類的列舉值。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> 按鈕<br /> 出現在工具列上的標準命令 (通常是 iconic 按鈕) 、功能表和內容功能表。<br /><br /> MenuButton<br /> 不會執行命令，但是會產生另一個功能表的功能表項目。<br /><br /> SplitDropDown<br /> 控制項，例如 Microsoft Word 中標準工具列上的 [復原] 和 [重做] 按鈕。|  
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Parent 元素](../extensibility/parent-element.md)|選擇性。 按鈕的父元素。|  
|[Icon 元素](../extensibility/icon-element.md)|選擇性。 與按鈕相關聯的圖示。|  
|[Command Flag 元素](../extensibility/command-flag-element.md)|必要。 按鈕的有效 CommandFlag 值如下所示。<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextCoNtextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings 元素](../extensibility/strings-element.md)|必要。 必須定義子 [ButtonText 元素](../extensibility/buttontext-element.md) 。|  
|Annotation|選擇性批註。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組按鈕元素。|  
  
## <a name="example"></a>範例  
 下列範例會在 .vsct 檔案中定義一個按鈕。  
   
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
