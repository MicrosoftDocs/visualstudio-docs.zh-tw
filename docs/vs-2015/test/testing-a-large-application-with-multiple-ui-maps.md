---
title: 測試含有多個 UI 對應的大型應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 24
ms.author: gewarren
manager: douge
ms.openlocfilehash: 40dae630f39597549f27c0aa77685d00e5ddd7ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487911"
---
# <a name="testing-a-large-application-with-multiple-ui-maps"></a>測試含有多個 UI 對應的大型應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[測試含有多個 UI 對應的大型應用程式](https://docs.microsoft.com/visualstudio/test/testing-a-large-application-with-multiple-ui-maps)。  
  
本主題討論如何使用自動程式化 UI 測試，透過多個 UI 對應來測試大型應用程式。  
  
 **需求**  
  
-   Visual Studio 企業版  
  
 當您建立新的自動程式化 UI 測試時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 測試架構預設會在 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 類別中產生測試的程式碼。 如需如何錄製自動程式碼 UI 測試的詳細資訊，請參閱[建立自動程式碼 UI 測試](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)和[自動程式碼 UI 測試的結構](../test/anatomy-of-a-coded-ui-test.md)。  
  
 為 UI 對應產生的程式碼會針對與測試互動的每個物件各包含一個類別。 針對每個產生的方法，系統會專門為該方法產生方法參數的附屬類別。 如果您的應用程式中有大量物件、頁面、表單和控制項，UI 對應可能會變得非常大。 此外，如果多人處理測試，只有單一大型 UI 對應檔的應用程式會變得不便使用。  
  
 使用多個 UI 對應檔可提供下列優點：  
  
-   每個對應可與一個應用程式邏輯子集相關聯。 這樣會更容易管理變更。  
  
-   每個測試人員可以處理應用程式的一部分並簽入其程式碼，而不妨礙處理應用程式其他部分的其他測試人員。  
  
-   您可採累加的方式擴增應用程式 UI，對 UI 其他部分之測試的影響可降至最低。  
  
## <a name="do-you-need-multiple-ui-maps"></a>您是否需要多個 UI 對應？  
 請在下列幾種情況下建立多個 UI 對應：  
  
-   一起執行邏輯作業的多組複雜的複合 UI 控制項，例如網站上的註冊網頁或購物車的購買網頁。  
  
-   從應用程式的多點存取的獨立一組控制項，例如具有數頁作業的精靈。 如果精靈的每一頁都特別複雜，您可以為每一頁各建立一個 UI 對應。  
  
## <a name="adding-multiple-ui-maps"></a>加入多個 UI 對應  
  
#### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>將 UI 對應加入至自動程式化 UI 測試專案  
  
1.  在方案總管的自動程式碼 UI 測試專案中，建立資料夾以儲存所有 UI 對應、以滑鼠右鍵按一下自動程式碼 UI 測試專案檔、指向 [新增]，然後選擇 [新增資料夾]。 例如，您可以將它命名為 `UIMaps`。  
  
     新資料夾隨即顯示在自動程式化 UI 測試專案底下。  
  
2.  以滑鼠右鍵按一下 `UIMaps` 資料夾，並指向 [新增]，然後選擇 [新增項目]。  
  
     隨即顯示 [ 新增項目] 對話方塊。  
  
    > [!NOTE]
    >  您必須在自動程式化 UI 測試專案中，才能加入新的自動程式化 UI 測試對應。  
  
3.  從清單中選取 [自動程式碼 UI 測試對應]。  
  
     在 [名稱] 方塊中，輸入新 UI 對應的名稱。 使用該對應將代表的元件或頁面名稱，例如， `HomePageMap`。  
  
4.  選擇 [新增]。  
  
     [[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]] 視窗會最小化，而 [自動程式碼 UI 測試產生器] 對話方塊隨即顯示。  
  
5.  錄製第一個方法的動作，然後選擇 [產生程式碼]。  
  
6.  當您已錄製第一個元件或頁面的所有動作和判斷提示，並將它們群組在方法中之後，請關閉 [自動程式碼 UI 測試產生器] 對話方塊。  
  
7.  繼續建立 UI 對應。 錄製動作和判斷提示，將它們群組在每個元件的方法中，然後產生程式碼。  
  
 在許多情況下，應用程式的最上層視窗對所有精靈、表單和頁面會保持固定。 雖然每個 UI 對應都有最上層視窗的類別，但所有對應可能都會參考應用程式所有元件執行所在的同一個最上層視窗。 自動程式碼 UI 測試會以階層方式由上而下，從最上層視窗開始搜尋控制項，因此在複雜應用程式中，實際的最上層視窗可能會重複出現在每個 UI 對應中。 如果實際的最上層視窗會重複，當該視窗變更時可能會需要多個修改。 當您在 UI 對應之間切換時，這可能會造成效能問題。  
  
 若要將這個影響降至最低，可以使用 `CopyFrom()` 方法，確定該 UI 對應中新的最上層視窗與主要最上層視窗相同。  
  
## <a name="example"></a>範例  
 下列範例是公用程式類別的一部分，此公用程式類別可用來存取在各種 UI 對應中產生之類別所代表的每個元件及其子控制項。  
  
 在這個範例中，名為 `Contoso` 的 Web 應用程式有首頁、產品網頁和購物車網頁。 上述每個網頁共用通用的最上層視窗，也就是瀏覽器視窗。 每個網頁都有 UI 對應，而且公用程式類別的程式碼類似如下：  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [使用使用者介面自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)   
 [建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [自動程式化 UI 測試的結構](../test/anatomy-of-a-coded-ui-test.md)



