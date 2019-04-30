---
title: 將 VSIX 封裝當地語系化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439763"
---
# <a name="localizing-vsix-packages"></a>將 VSIX 套件當地語系化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將 VSIX 封裝當地語系化藉由建立每個目標語言的 Extension.vsixlangpack 檔案並再將它們放入正確的資料夾。 安裝當地語系化的套件時，延伸模組的當地語系化的名稱會顯示與當地語系化的描述。 如果您提供當地語系化的授權檔案或指向當地語系化資訊的 URL，也會顯示它們。  
  
 如果內容 VSIX 封裝包含 VSPackage 將功能表命令或其他 UI，請參閱[當地語系化功能表命令](../extensibility/localizing-menu-commands.md)如需當地語系化新的 UI 項目。  
  
## <a name="directory-structure"></a>目錄結構  
 當使用者安裝延伸模組，**擴充功能和更新**檢查最高層級的 VSIX 封裝，其名稱符合 Visual Studio 電腦的地區設定目標的資料夾。 如果**擴充功能和更新**.vsixlangpack 找到檔案的資料夾中，它會取代該檔案的.vsixmanifest 檔案中的對應值的當地語系化的值。 正在安裝延伸模組時，會顯示這些值。 下列範例顯示 VSIX 封裝當地語系化為西班牙文 (ES-ES) 和法文 (FR-FR) 的目錄結構。  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types].xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
> 中的 VSIX 支援的專案範本[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]產生 VSIX 資訊清單並將它命名為 source.extension.vsixmanifest。 當 Visual Studio 會建置專案時，它會複製該檔案的內容到 Extension.VsixManifest VSIX 封裝中。  
  
## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack 檔案  
 Extension.vsixlangpack 檔案會遵循[VSIX 語言套件結構描述](../extensibility/vsx-language-pack-schema-reference.md)。 此結構描述[VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)根元素，而且這些包含四個子項目：[LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)， [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)， [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)，和[授權](../extensibility/license-element-vsix-language-pack-schema.md)。 這些子元素會對應至`Name`， `Description`， `MoreInfoURL`，以及`License`子項目的`Identifier`Extension.vsixmanifest 檔案項目。  
  
 當您建立 vsixlangpack 檔案時，您必須設定`Include in Vsix`屬性設`true`。 否則，會忽略的當地語系化的安裝文字。  
  
#### <a name="to-set-the-include-in-vsix-property"></a>若要設定包含在 Vsix 屬性  
  
1. 在 **方案總管**Extension.vsixlangpack 檔案中，按一下滑鼠右鍵，然後按一下 **屬性**。  
  
2. 在屬性方格中，按一下**Include in Vsix**，並將其值設定為`true`。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會示範 Extension.vsixmanifest 檔案，以及西班牙文的對應 Extension.vsixlangpack 檔案的相關部分。 如果 Visual Studio 電腦的地區設定目標設定為西班牙文語言套件中的值就會取代從資訊清單的值。  
  
### <a name="code"></a>程式碼  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSIX LanguagePack 元素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 專案範本](../extensibility/vsix-project-template.md)
