---
title: 通常用來擴充專案的物件 Catid |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 466a813ee905b75d2ca3f940dcf7040f8421c6fa
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512066"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>Catid 通常用來擴充專案的物件
下表列出可用來擴充的 Catid`Project`並`ProjectItem`自動化物件[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，和[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案。 在 定義這些 Catid *VSLangProj.olb*。  
  
## <a name="listing-of-catids"></a>列出的 Catid  
  
|名稱|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|  
  
## <a name="visual-basic-catids"></a>Visual Basic Catid  
 下表列出可用來擴充的 Catid[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]瀏覽的物件。 所有以定義它們*VSLangProj.olb*。  
  
|名稱|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|  
  
## <a name="visual-c-catids"></a>Visual C# Catid  
 下列的 Catid 可用來擴充[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]瀏覽的物件。 所有以定義它們*VSLangProj.olb*。  
  
|名稱|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|  
  
## <a name="c-catids"></a>C + + Catid  
 下列[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案的系統中的型別程式庫中未公開 Catid [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003年和一定要包含在您的程式碼中，每當您想要擴充這些專案物件。 中的後續版本中的類型程式庫會包含這些 Catid [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
|名稱|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 下列程式碼範例示範如何撰寫程式的程式碼中的這些 Catid。  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 下列[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案的系統中的型別程式庫中也未公開 Catid [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003年和一定要包含在您的程式碼中，每當您想要擴充這些專案物件。 這些 Catid 是僅適用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].NET 2003年而且不會用於較新版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
|名稱|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|  
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 下列程式碼範例示範如何撰寫程式的程式碼中的這些 Catid:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Guid[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型會顯示下表中。  
  
|專案類型|GUID|  
|------------------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F-C81C-45F6-A57F-5ABD9991F28F}|  
  
## <a name="see-also"></a>另請參閱  
 [將專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)