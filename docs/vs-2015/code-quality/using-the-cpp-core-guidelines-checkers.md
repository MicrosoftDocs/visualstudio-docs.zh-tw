---
title: 使用 c + + Core Guidelines 檢查工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799557"
---
# <a name="using-the-c-core-guidelines-checkers"></a>使用 c + + Core Guidelines 檢查工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C + + Core Guidelines 是可攜性的集合的指導方針、 規則和關於 c + + 專家和設計工具所建立的 c + + 中撰寫程式碼的最佳作法。  Visual Studio 現在支援增益集封裝，建立其他規則的程式碼分析工具，以檢查您的程式碼與 c + + Core Guidelines 的合規性，並提供改善建議。  
  
## <a name="the-c-core-guidelines-project"></a>C + + Core Guidelines 的專案  
 C + + Core Guidelines Bjarne Stroustrup 和其他人所建立，是安全且有效地使用新式 c + + 的指南。 指導方針強調靜態型別安全和資源的安全。 它們會找出方法來消除或是減少最容易出錯的組件的語言，並建議如何簡化您的程式碼，以及更好的效能，可靠的方式。 這些指導方針是由標準 c + + Foundation 維護。 若要進一步了解，請參閱文件中， [c + + Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)，並存取 c + + Core Guidelines 的文件的專案檔上[GitHub](https://github.com/isocpp/CppCoreGuidelines)。  
  
 Microsoft 支援的 c + + Core Guidelines 的工作，藉由 c + + Core Check 程式碼分析規則設定，您可以使用 Nuget 套件新增至您的專案。 封裝名為 Microsoft.CppCoreCheck，且可在[ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck)。 此封裝需要有至少安裝 Visual Studio 2015 Update 1。  
  
 封裝也會安裝為相依性，僅限標頭的指導方針的支援程式庫 (GSL) 另一個套件。 GSL 也是在 GitHub 上的可用[ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)。  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>啟用程式碼分析的 c + + Core Check 指導方針  
 若要啟用 c + + Core Check 程式碼分析工具，將 Microsoft.CppCoreCheck NuGet 套件安裝到您想要在 Visual Studio 中檢查每個 c + + 專案。  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>若要將 Microsoft.CppCoreCheck 套件新增至您的專案  
  
1. 在 [**方案總管] 中**，以滑鼠右鍵按一下您想要將封裝加入方案中開啟您專案的內容功能表。 選擇**管理 NuGet 套件**來開啟**NuGet 套件管理員**。  
  
2. 在  **NuGet 套件管理員**視窗中，搜尋 Microsoft.CppCoreCheck。  
  
    ![Nuget 套件管理員 視窗會顯示封裝 CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. 選取 Microsoft.CppCoreCheck 封裝，然後選擇**安裝** 按鈕，將規則新增至您的專案。  
  
   NuGet 套件會將您的專案上啟用程式碼分析時，會叫用您專案中的其他的 MSBuild.targets 檔案。 這個.targets 檔案會將 c + + Core Check 規則做為額外的延伸模組加入至 Visual Studio 程式碼分析工具。  
  
   您也可以選取您的專案上啟用程式碼分析**建置時啟用程式碼分析**核取方塊**程式碼分析**一節**屬性頁**對話方塊您的專案。  
  
   ![程式碼分析的一般設定 屬性頁](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C + + Core Check 規則成為預設的規則集執行程式碼分析已啟用時的一部分。 由於 c + + Core Check 規則在開發期間，某些規則可能無法供使用的所有程式碼，但在開發期間可能有用的資訊。 這些規則會發行為實驗性。 您可以選擇是否要為您的專案屬性中執行的已釋出或實驗性的規則。  
  
   ![程式碼分析延伸模組設定的屬性頁](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   若要啟用或停用 c + + Core Check 規則集，請開啟**屬性頁**為您的專案 對話方塊。 底下**組態屬性**，展開**程式碼分析**，**延伸**。 下拉式清單中控制項旁**啟用 c + + Core Check （發行）** 或**啟用 c + + Core Check （實驗性）**，選擇**是**或是**否**。 選擇 **[確定]** 或是**套用**以儲存變更。  
  
## <a name="check-types-bounds-and-lifetimes"></a>檢查類型、 範圍和存留期  
 C + + Core Check 套件目前包含的西洋棋[型別安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type)，[界限安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)，並[存留期安全](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime)設定檔。  
  
 以下是範例的 c + + Core Check 規則可以找到的問題種類：  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 此範例會示範幾個可以找到的 c + + Core Check 規則的警告：  
  
- C26494 是規則 Type.5： 一律初始化物件。  
  
- C26485 是規則 Bounds.3： 沒有陣列到指標 」 衰減。  
  
- C26481 是規則 Bounds.1： 不使用指標算術。 請改用 `span`。  
  
  如果安裝和啟用，當您編譯此程式碼時前, 兩個警告皆為輸出，但會隱藏第三個 c + + Core Check 的程式碼分析規則集。 以下是範例程式碼的組建輸出：  
  
  **1 >---已開始建置： 專案： CoreCheckExample、 組態： Debug Win32-**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj]-> [C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj]-> [C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (完整 PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6)： 警告 C26494： 變數 'arr' 是 uninitializ**  
**ed.一律會初始化物件。(type.5: http://go.microsoft.com/fwlink/p/?Link**  
**識別碼 = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7)： 警告 C26485： 運算式 'arr': 沒有陣列**  
 **指標 」 衰減。(bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== 建置： 1 成功、 0 失敗、 0 最新狀態，0 個略過 ===** 的 c + + Core Guidelines 是否有可協助您撰寫更好且更安全的程式碼。 不過，如果您有一個規則或設定檔不應該套用的位置執行個體，很容易就能直接在程式碼中隱藏它。 您可以使用`gsl::suppress`讓 c + + Core Check 偵測和報告任何違反規則，以下列程式碼區塊中的屬性。 您可以將標記個別的陳述式，以隱藏特定的規則。 您甚至可以隱藏整個 「 範圍 」 設定檔，藉由撰寫`[[gsl::suppress(bounds)]]`且不包含特定的規則數目。  
  
## <a name="use-the-guideline-support-library"></a>使用指導方針的支援程式庫  
 Microsoft.CppCoreCheck NuGet 套件也會安裝包含 Microsoft 實作的指導方針的支援程式庫 (GSL) 中的封裝。 GSL 中也會提供獨立表單[ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl)。 如果您想要遵循核心指導方針，有幫助。 此程式庫。 GSL 包含可讓您以更安全的替代項目取代出錯建構的定義。 例如，您可以取代`T*, length`的參數組`span<T>`型別。 GSL 開放原始碼，因此如果您想要看一下程式庫來源註解，或參與編輯，專案，請參閱[ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)。



