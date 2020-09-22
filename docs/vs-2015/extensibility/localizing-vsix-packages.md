---
title: 當地語系化 VSIX 套件 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838886"
---
# <a name="localizing-vsix-packages"></a>將 VSIX 套件當地語系化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以針對每個目的語言建立 vsixlangpack 檔案，然後將它們放在正確的資料夾中，以當地語系化 VSIX 套件。 安裝當地語系化的封裝時，會連同當地語系化的描述一起顯示延伸模組的當地語系化名稱。 如果您提供當地語系化的授權檔案，或指向當地語系化資訊的 URL，也會顯示這些檔案。  
  
 如果您的 VSIX 套件包含可新增功能表命令或其他 UI 的 VSPackage，請參閱 [當地語系化功能表命令](../extensibility/localizing-menu-commands.md) 以取得當地語系化新 UI 元素的相關資訊。  
  
## <a name="directory-structure"></a>目錄結構  
 當使用者安裝擴充功能時， **延伸模組和更新** 會檢查 VSIX 封裝的最上層是否有名稱符合目的電腦 Visual Studio 地區設定的資料夾。 如果 **延伸模組和更新** 在資料夾中找到 vsixlangpack 檔案，則會將該檔案中的當地語系化值取代為 extension.vsixmanifest 檔案中的對應值。 當擴充功能安裝完成時，會顯示這些值。 下列範例會顯示當地語系化為西班牙文 (es) 和法文 (fr-fr) 之 VSIX 封裝的目錄結構。  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Vsixlangpack  
  
 fr-FR  
  
 Vsixlangpack  
  
> [!NOTE]
> 中支援 VSIX 的專案範本 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 會產生 vsix 資訊清單，並將其命名為 extension.vsixmanifest。 當 Visual Studio 建立專案時，它會將該檔案的內容複寫到 VSIX 封裝的 Extension.vsixmanifest 中。  
  
## <a name="the-extensionvsixlangpack-file"></a>Vsixlangpack 檔案  
 Vsixlangpack 檔案會遵循 [VSIX 語言套件架構](../extensibility/vsx-language-pack-schema-reference.md)。 此架構具有 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) 根項目，以及下列四個子項目： [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)、 [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)、 [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)和 [License](../extensibility/license-element-vsix-language-pack-schema.md)。 這些子項目會對應至 `Name` extension.vsixmanifest 檔案之元素的、 `Description` 、 `MoreInfoURL` 和 `License` 子項目 `Identifier` 。  
  
 當您建立 vsixlangpack 檔案時，必須將屬性設定 `Include in Vsix` 為 `true` 。 否則，將會忽略當地語系化的安裝文字。  
  
#### <a name="to-set-the-include-in-vsix-property"></a>若要設定 Include in Vsix 屬性  
  
1. 在 **方案總管**中，以滑鼠右鍵按一下 vsixlangpack 檔案，然後按一下 [ **屬性**]。  
  
2. 在屬性方格中，按一下 [ **在 Vsix 中包含**]，並將其值設定為 `true` 。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會顯示 extension.vsixmanifest 檔案的相關部分，以及適用于西班牙文的對應副檔名 vsixlangpack 檔案。 如果目的電腦的 Visual Studio 地區設定設為西班牙文，則語言套件中的值會取代資訊清單中的值。  
  
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
  
 [Vsixlangpack]  
  
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
 [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 專案範本](../extensibility/vsix-project-template.md)
