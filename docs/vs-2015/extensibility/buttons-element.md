---
title: 按鈕項目 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0a17e3580b238c63a23e5943e98afbbb9268b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941915"
---
# <a name="buttons-element"></a>Buttons 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

群組[ 按鈕](../extensibility/button-element.md)項目，表示個別的命令。  
  
## <a name="syntax"></a>語法  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|分組按鈕項目。|  
|[Button 元素](../extensibility/button-element.md)|定義使用者可以互動的命令。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 [VSPackage] 工具列上的命令的集合。|  
  
## <a name="example"></a>範例  
  
```  
<Buttons>  
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">  
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>  
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>  
    <Strings>  
      <ButtonText>C# Command Sample</ButtonText>  
    </Strings>  
  </Button>  
</Buttons>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
