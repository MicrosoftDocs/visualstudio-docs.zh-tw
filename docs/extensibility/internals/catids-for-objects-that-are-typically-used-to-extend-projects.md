---
title: 通常用於擴充項目的物件的 CATID |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5754e53f24731eb44dba128ccfcf4b474e833d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709870"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>通常用於延伸項目的物件的 CATID
下表`Project`列出了用於`ProjectItem`[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]擴[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]充和專案的物件[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]的 CATID。 這些 CATId 在*VSLangProj.olb*中定義。

## <a name="listing-of-catids"></a>CATID 清單

|名稱|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|[610D4614-D0D5-11D2-8599-006097C68E81]|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|[610D4615-D0D5-11D2-8599-006097C68E81]|

## <a name="visual-basic-catids"></a>視覺基本 CAT
 下表列出了用於擴展[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]瀏覽物件的 CATID。 它們都定義在*VSLangProj.olb。*

|名稱|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|[E0FDC879-C32A-4751-A3D3-0B3824BD575F]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|[67F8DD11-14EB-489b-87F0-F01C52AF3870]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|[EA5BD05D-3C72-40A5-95A0-28A2773311CA]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5]|

## <a name="visual-c-catids"></a>視覺 C# CAT
 以下 CATID 可[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]用於擴展 瀏覽物件。 它們都定義在*VSLangProj.olb。*

|名稱|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|[4EF9F003-DE95-4d60-96B0-212979F2A857]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|[A12CE10A-227F-4963-ADB6-3A43388513CA]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|[8D58E6AF-ED4E-48B0-8C7B-C74EF0735451]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C]|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|[2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27]|

## <a name="c-catids"></a>C++ CATIDs
 以下[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案系統 CATID 不會在 .NET[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]2003 中的類型庫中公開,並且每當要擴展這些專案物件時,都必須包含在代碼中。 這些 CATID 將包含在 以後[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本中的類型 庫中。

|名稱|GUID|
|----------|----------|
|`CVCProjectNode`|[EE8299CB-19B6-4f20-ABEA-E1FD9A33B683]|
|`CVCFolderNode`|[EE8299CA-19B6-4f20-ABEA-E1FD9A33B683]|
|`CVCFileNode`|[EE8299C9-19B6-4f20-ABEA-E1FD9A33B683]|

 以下代碼示例演示如何在代碼中對這些 CATID 進行程式設計。

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 以下[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案系統 CATID 也不會在 .NET[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]2003 中的類型庫中公開,並且每當要擴展這些專案物件時,都必須包含在代碼中。 這些 CATI[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]僅在 .NET 2003[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中可用,在的更高版本中將不可用。

|名稱|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|[FE8299C9-19B6-4f20-ABEA-E1FD9A33B683]|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|[9E8182D3-C60A-44f4-A74B-14C90EF9CACE]|
|`CVCReferences`|[FE8299CA-19B6-4f20-ABEA-E1FD9A33B683]|

 以下代碼範例展示如何在代碼中對這些 CATID 進行程式設計:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]項目類型的 GUID[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]顯示在下表中。

| 專案類型 | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | [FAE04EC0-301F-11D3-BF4B-00C04F79EFBC] |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | [F184B08F-C81C-45F6-A57F-5ABD9991F28F] |

## <a name="see-also"></a>另請參閱
- [新增項目和項目項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
