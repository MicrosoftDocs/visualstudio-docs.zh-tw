---
title: Combo 元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00ecabcf90e63b18961a828c12ae300be359b5a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839982"
---
# <a name="combo-element"></a>Combo 元素
定義會出現在下拉式方塊中的命令。 有四種下拉式方塊，如下所示： 下拉式組合、 DynamicCombo、 IndexCombo 和 MRUCombo。  
  
## <a name="syntax"></a>語法  
  
```xml 
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼的命令識別項的識別碼。|  
|defaultWidth|必要。 指定下拉式方塊的像素寬度的整數。|  
|idCommandList|必要。 擷取要顯示在下拉式方塊中的項目清單傳送至作用中的命令目標識別碼。 識別碼會在相同的 GUID 範圍內，做為控制項。|  
|priority|選擇性。 數值，指定的優先權。|  
|類型|選擇性。 列舉的值，指定的按鈕類型。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> 下拉式組合<br /> VSPackage 是負責填入這個下拉式方塊的內容。 使用者無法將任何項目在這個下拉式表單的文字方塊中輸入。<br /><br /> DynamicCombo<br /> VSPackage 是負責填入這個下拉式方塊的內容。 使用者可以編輯此組合，並也在其中選取項目。<br /><br /> IndexCombo<br /> 只是它的 DynamicCombo 相同引發項目，而不是它的文字的索引。<br /><br /> MRUCombo<br /> 填入代表 VSPackage 的整合式的開發環境 (IDE)。  使用者可以編輯此下拉式方塊中。 IDE 會記住最多每下拉式方塊的最後 16 個項目。<br /><br /> 當使用者在下拉式方塊中，選取的項目，或輸入新的項目時，則 IDE 會通知適當的 VSPackage。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代|選擇性。 按鈕的父項目。|  
|CommandFlag|必要。 請參閱[Command flag 元素](../extensibility/command-flag-element.md)。 CommandFlag 按鈕有效值，如下所示。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -篩選鍵<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|字串|必要。 請參閱[Strings 元素](../extensibility/strings-element.md)。 必須定義子 ButtonText 元素。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 [VSPackage] 工具列上的命令的集合。|  
  
## <a name="example"></a>範例  
  
```xml  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
