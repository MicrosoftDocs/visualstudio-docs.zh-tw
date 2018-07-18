---
title: 命令項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d905914c9819671cf8c77d81ec8d51302467a9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108478"
---
# <a name="commands-element"></a>Commands 元素
表示 VSPackage 工具列上的命令的集合。 集合可以擁有最多五個小節，如下： 功能表、 群組、 按鈕、 組合和點陣圖。  
  
 每個小節子元素，例如\<功能表 >，由 GUID，而且數字識別元組的唯一的命令識別碼。 GUID 識別的 「 命令集 」，並用於群組邏輯上相關的命令。 VSPackage 應該定義自己的命令集，避免發生衝突，會由其他 Vspackage 的命令識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|套件|GUID，識別 VSPackage 提供的命令。<br /><br /> 例如，封裝 ="guidVsPackage1Pkg"。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Menus 元素](../extensibility/menus-element.md)|定義所有實作 VSPackage 的功能表。|  
|[Groups 元素](../extensibility/groups-element.md)|包含在 VSPackage 中定義的命令群組的項目。|  
|[Buttons 元素](../extensibility/buttons-element.md)|群組按鈕項目。|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|群組點陣圖項目。|  
|[Combos 元素](../extensibility/combos-element.md)|群組下拉式項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表 VSPackage 提供給 IDE 的命令的所有項目。 可能的項目是功能表項目、 功能表、 工具列和下拉式方塊。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用[Commands 元素](../extensibility/commands-element.md)。  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)