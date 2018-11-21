---
title: 符號項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9bccb3874d5b85a8a69288e2bf44adb14b5b3f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783241"
---
# <a name="symbols-element"></a>Symbols 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

定義 Guid 和 Id，可供其他 VSCT 項目。 Unmanaged 程式碼，這項資訊通常來自所指定的標頭檔[Extern 元素](../extensibility/extern-element.md)。 Managed 程式碼會使用項目的子項目符號來定義這項資訊。  
  
 如果您從現有的.cto 檔建立.vsct 檔，就會產生符號做為符號項目的子系。 如需詳細資訊，請參閱[How to： 建立。從現有的 Vsct 檔案。Cto 檔案](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)。  
  
 Symbols 元素不應該與混淆[定義的項目](../extensibility/define-element.md)，其定義前置處理器所使用的名稱 / 值組。  
  
## <a name="syntax"></a>語法  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|無||  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|GuidSymbol|定義 GUID 符號。 GuidSymbol 有兩個必要的屬性： 名稱和值。 名稱為的符號名稱，值為 GUID 做為字串值。<br /><br /> 例如：\<GuidSymbol 名稱 ="guidVsPackage1Pkg"value ="{c5f54698-101a-4846-84d3-dc748f9cd848}"/ >|  
|IDSymbol|定義符號。 IDSymbol 有兩個必要的屬性： 名稱和值。 名稱為符號，名稱和值是字串形式的符號值。<br /><br /> 例如：\<IDSymbol 名稱 ="MyMenuGroup"value ="0x1020"/ >|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|.Vsct 檔的根項目。|  
  
## <a name="example"></a>範例  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

