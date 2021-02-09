---
title: '&lt;啟動載入器 &gt;)  (PackageFiles 元素 |Microsoft Docs'
description: 瞭解 PackageFiles 元素，其中包含 PackageFile 元素，這些元素會定義命令元素所執行的安裝套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0fbf76fec604819d7944a7b54fa4b2421e37c111
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925358"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;啟動載入器 &gt;)  (PackageFiles 元素
`PackageFiles`元素包含 `PackageFile` 元素，這些元素會定義作為元素結果執行的安裝套件 `Command` 。

## <a name="syntax"></a>Syntax

```xml
<PackageFiles
    CopyAllPackageFiles
>
    <PackageFile
        Name
        HomeSite
        CopyOnBuild
        PublicKey
        Hash
    />
</PackageFiles>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `PackageFiles` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`CopyAllPackageFiles`|選擇性。 如果設定為 `false` ，則安裝程式只會下載從元素參考的檔案 `Command` 。 如果設定為 `true` ，則會下載所有檔案。<br /><br /> 如果設定為 `IfNotHomesite` ，則安裝程式的行為會如同如果 `False` `ComponentsLocation` 設定為 `HomeSite` ，否則會與相同的行為 `True` 。 這項設定有助於讓本身啟動載入器的套件在 HomeSite 案例中執行自己的行為。<br /><br /> 預設為 `true`。|

## <a name="packagefile"></a>PackageFile
 `PackageFile`元素是元素的子系 `PackageFiles` 。 `PackageFiles`元素至少必須有一個 `PackageFile` 元素。

 `PackageFile` 具有下列屬性。

| 屬性 | 描述 |
|---------------| - |
| `Name` | 必要。 封裝檔案的名稱。 這是 `Command` 元素在定義封裝安裝的條件時，將會參考的名稱。 此值也會用來做為資料表中的索引鍵， `Strings` 以取得工具（例如 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 將用來描述封裝）的當地語系化名稱。 |
| `HomeSite` | 選擇性。 在遠端伺服器上封裝的位置（如果不包含在安裝程式中的話）。 |
| `CopyOnBuild` | 選擇性。 指定啟動載入器是否應在組建階段將封裝檔案複製到磁片上。 預設值是 true。 |
| `PublicKey` | 封裝之憑證簽署者的加密公開金鑰。 如果使用，則為必要 `HomeSite` ，否則為選擇性。 |
| `Hash` | 選擇性。 封裝檔案的 SHA1 雜湊。 這是用來在安裝時驗證檔案的完整性。 如果無法從封裝檔案計算相同的雜湊，將不會安裝封裝。 |

## <a name="example"></a>範例
 下列程式碼範例會定義 .NET Framework 可轉散發套件及其相依性的套件，例如 Windows Installer。

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>另請參閱
- [\<Product> 元素](../deployment/product-element-bootstrapper.md)
- [\<Package> 元素](../deployment/package-element-bootstrapper.md)
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)