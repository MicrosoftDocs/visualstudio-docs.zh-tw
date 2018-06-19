---
title: CA2210：組件應包含有效的強式名稱
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b7fb5f55ee345fa47a4a4510fe8121b82d1c0ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919634"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210：組件應包含有效的強式名稱
|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 未以強式名稱簽署組件無法驗證強式名稱，或強式名稱不是有效沒有目前登錄設定的電腦。

## <a name="rule-description"></a>規則描述
 此規則會擷取並驗證組件的強式名稱。 如果下列任一項為真，就會發生違規：

-   組件沒有強式名稱。

-   組件已簽署後遭修改。

-   組件是延遲簽署。

-   不正確地簽署組件，或簽章失敗。

-   組件需要登錄設定，才能通過驗證。 例如，強式名稱工具 (Sn.exe) 用來略過驗證的組件。

 強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。 除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。 如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，通用語言執行平台可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。 沒有強式名稱的組件具有下列缺點：

-   無法驗證該組件的來源。

-   Common language runtime 無法警告使用者組件的內容已被竄改。

-   它無法載入全域組件快取。

 請注意，載入並分析延遲簽署組件，您必須停用驗證的組件。

## <a name="how-to-fix-violations"></a>如何修正違規
 **若要建立的金鑰檔案**

 使用下列程序的其中一個：

-   使用所提供的組件連結器工具 (Al.exe) [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK。

-   如[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]v1.0 或 v1.1，使用<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>或<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>屬性。

-   如[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，使用`/keyfile`或`/keycontainer`編譯器選項[/KEYFILE （指定金鑰或金鑰組簽署組件）](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)或[/KEYCONTAINER （指定金鑰容器以簽署組件）](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly)在 c + + 連結器選項)。

 **您在 Visual Studio 中的強式名稱組件簽署**

1.  在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，開啟您的方案。

2.  在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**屬性。**

3.  按一下**簽署**索引標籤，然後選取**簽署組件**核取方塊。

4.  從**選擇強式名稱金鑰檔**，選取**新增**。

     **建立強式名稱金鑰**視窗會顯示。

5.  在**金鑰檔名稱**，輸入強式名稱金鑰的名稱。

6.  選擇是否要保護的金鑰使用密碼，然後按一下 **確定**。

7.  在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**建置**。

 **若要使用 Visual Studio 外部的強式名稱組件簽章**

-   使用強式名稱工具 (Sn.exe) 所提供的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]SDK。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](/dotnet/framework/tools/sn-exe-strong-name-tool)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有隱藏此規則的警告，如果組件的環境中使用其中竄改的內容不是問題。

## <a name="see-also"></a>另請參閱
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> [如何： 簽署為強式名稱組件](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name) [Sn.exe （強式名稱工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)