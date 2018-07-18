---
title: 下拉式項目 |Microsoft 文件
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
ms.openlocfilehash: ca91102467755610144e4d24405e89ace5a013b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100935"
---
# <a name="combo-element"></a>下拉式項目
定義了出現在下拉式方塊中的命令。 有四種下拉式方塊的如下所示： 下拉式組合、 DynamicCombo、 IndexCombo 和 MRUCombo。  
  
## <a name="syntax"></a>語法  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼命令識別項的識別碼。|  
|defaultWidth|必要。 整數，指定像素寬度下拉式方塊。|  
|idCommandList|必要。 擷取要顯示在下拉式方塊中的項目清單會傳送至作用中的命令目標識別碼。 識別碼會以和控制項的 GUID 範圍相同。|  
|priority|選擇性。 數值，指定的優先權。|  
|類型|選擇性。 列舉的值，指定按鈕的型別。<br /><br /> 如果沒有指定，會使用按鈕。<br /><br /> 下拉式組合<br /> VSPackage 會負責填入下拉式方塊的內容。 使用者無法在此下拉式清單中的文字方塊中輸入任何內容。<br /><br /> DynamicCombo<br /> VSPackage 會負責填入下拉式方塊的內容。 使用者可以編輯此組合，也在其中選取項目。<br /><br /> IndexCombo<br /> 只是它 DynamicCombo 相同引發項目，而不是它的文字的索引。<br /><br /> MRUCombo<br /> 填入代表 VSPackage 的整合式的開發環境 (IDE)。  使用者可以在此下拉式方塊中編輯。 IDE 會記住到每個下拉式方塊的最後 16 個項目。<br /><br /> 當使用者在下拉式方塊中，選取的項目，或輸入新項目時，IDE 會通知適當的 VSPackage。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|父代|選擇性。 按鈕的父項目。|  
|CommandFlag|必要。 請參閱[命令旗標的項目](../extensibility/command-flag-element.md)。 CommandFlag 按鈕的有效值，如下所示。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -篩選鍵<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|字串|必要。 請參閱[字串項目](../extensibility/strings-element.md)。 必須定義子 ButtonText 項目。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令的集合。|  
  
## <a name="example"></a>範例  
  
```  
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
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)