---
title: "將 COM 元件使用 ClickOnce 部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a63073e86c3584253e67bf4d77f43006104de075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-com-components-with-clickonce"></a>使用 ClickOnce 部署 COM 元件
傳統 COM 元件的部署一直困難的工作。 元件必須全域註冊，因此可能會導致非預期的副作用重疊的應用程式之間。 這種情況通常不是.NET Framework 應用程式中的問題因為彼此完全隔離的應用程式或元件的並存相容。 Visual Studio 可讓您部署獨立的 COM 元件，Windows XP 或更高版本的作業系統上。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]提供簡單而安全機制，可將.NET 應用程式部署。 不過，如果您的應用程式使用傳統 COM 元件，您必須採取其他步驟，才能將其部署。 本主題描述如何部署獨立的 COM 元件和參考原生元件 （例如，從 Visual Basic 6.0 或 Visual c + +）。  
  
 如需部署獨立的 COM 元件的詳細資訊，請參閱 「 簡化應用程式部署與[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]和免註冊 COM"在[http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)。  
  
## <a name="registration-free-com"></a>免註冊 COM  
 免註冊 COM 是用於部署和啟動獨立的 COM 元件的新技術。 其運作方式是將所有元件的類型程式庫和註冊資訊，通常會安裝成在系統登錄中稱為資訊清單是 XML 檔案儲存在與應用程式相同的資料夾中。  
  
 隔離的 COM 元件需要它開發人員的電腦上註冊，但它並沒有要在終端使用者電腦上登錄。 若要隔離的 COM 元件，您只需要設定它的參考**隔離**屬性**True**。 根據預設，這個屬性設定為**False**，指出，它應該會被視為已註冊的 COM 參考。 如果這個屬性是**True**，它會造成要在建置階段，此元件產生的資訊清單。 它也會造成要在安裝期間複製到應用程式資料夾的對應檔案。  
  
 資訊清單產生器遇到隔離的 COM 參考時，會列舉所有`CoClass`項目中的元件類型程式庫，比對每個項目取代為其對應的登錄資料，並產生資訊清單的所有 COM 定義類型程式庫檔案中的類別。  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>免註冊 COM 元件使用 ClickOnce 部署  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署技術非常適合用來部署隔離的 COM 元件，因為兩者[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]和免註冊 COM 需要元件有資訊清單，才能進行部署。  
  
 通常，元件作者應該提供資訊清單。 如果沒有，不過，Visual Studio 是能夠產生資訊清單會自動針對 COM 元件。 資訊清單產生期間，會執行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]發行處理序; 如需詳細資訊，請參閱[發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。 這項功能也可讓您充分利用您先前的開發環境，例如 Visual Basic 6.0 中撰寫的舊版元件。  
  
 有兩種方式，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 COM 元件：  
  
-   用於啟動載入器部署 COM 元件;這適用於所有支援平台。  
  
-   使用原生元件隔離 (也稱為免註冊 COM) 部署。 不過，這僅用於在 Windows XP 或更高版本的作業系統。  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>隔離和部署簡單的 COM 元件的範例  
 為了示範免註冊 COM 元件的部署，此範例將參考隔離原生 COM 元件使用 Visual Basic 6.0 建立的 Visual Basic 中建立 Windows 架構應用程式和部署使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。  
  
 首先，您必須建立原生的 COM 元件：  
  
##### <a name="to-create-a-native-com-component"></a>若要建立原生的 COM 元件  
  
1.  從使用 Visual Basic 6.0**檔案**功能表上，按一下 **新增**，然後**專案**。  
  
2.  在**新專案**對話方塊中，選取**Visual Basic**節點，然後選取**ActiveX DLL**專案。 在 [名稱] 方塊中，輸入 `VB6Hello`。  
  
    > [!NOTE]
    >  免註冊 COM; 只能 ActiveX DLL 和 ActiveX 控制項的專案類型支援不支援 ActiveX EXE 和 ActiveX 文件的專案類型。  
  
3.  在**方案總管 中**，連按兩下**Class1.vb**在文字編輯器開啟。  
  
4.  Class1.vb 中加入下列程式碼之後產生的程式碼`New`方法：  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  建立元件。 從**建置**功能表上，按一下 **建置方案**。  
  
> [!NOTE]
>  免註冊 COM 支援只 Dll 和 COM 控制專案類型。 您不能使用免註冊 COM Exe  
  
 現在您可以建立 Windows 架構應用程式，並加入 COM 元件的參考。  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>若要建立 Windows 架構應用程式使用 COM 元件  
  
1.  使用 Visual Basic 中，從**檔案**功能表上，按一下 **新增**，然後**專案**。  
  
2.  在**新專案**對話方塊中，選取**Visual Basic**節點，然後選取**Windows 應用程式**。 在 [名稱] 方塊中，輸入 `RegFreeComDemo`。  
  
3.  在**方案總管 中**，按一下 **顯示所有檔案** 按鈕以顯示專案參考。  
  
4.  以滑鼠右鍵按一下**參考**節點，然後選取**加入參考**從內容功能表。  
  
5.  在**加入參考**對話方塊中，按一下 **瀏覽**索引標籤上，瀏覽至 VB6Hello.dll，然後選取它。  
  
     A **VB6Hello**參考出現在 [參考] 清單中。  
  
6.  指向**工具箱**，選取**按鈕**控制項，然後將它拖曳至**Form1**表單。  
  
7.  在**屬性**視窗中，設定按鈕的**文字**屬性**Hello**。  
  
8.  按兩下這個按鈕，加入處理常式程式碼，並在程式碼檔案中，加入程式碼，讓處理常式，如下所示：  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. 執行應用程式。 從**偵錯**功能表上，按一下 **開始偵錯**。  
  
 接下來，您必須找出控制項。 每個應用程式所使用的 COM 元件被以 COM 參考專案中。 這些參考會顯示在**參考**節點**方案總管 中**視窗。 (請注意，您可以將參考直接使用**加入參考**命令**專案**功能表上，或間接將 ActiveX 控制項拖曳至表單。)  
  
 下列步驟顯示如何隔離的 COM 元件並發佈更新的應用程式內含隔離的控制項：  
  
##### <a name="to-isolate-a-com-component"></a>若要找出 COM 元件  
  
1.  在**方案總管 中**，請在**參考**節點中，選取**VB6Hello**參考。  
  
2.  在**屬性**視窗中，變更的值**外掛式**屬性從**False**至**True**。  
  
3.  從**建置**功能表上，按一下 **建置方案**。  
  
 現在，您按下 F5，應用程式如預期般運作，，但它現在正在免註冊 com。 為了證明，請嘗試取消註冊 VB6Hello.dll 元件，並執行 Visual Studio IDE 外部 RegFreeComDemo1.exe。 當按一下按鈕時，這次它仍能運作。 如果您暫時重新命名應用程式資訊清單，它會一次失敗。  
  
> [!NOTE]
>  您可以暫時取消註冊，以模擬 COM 元件不存在。 開啟命令提示字元，請移至您的系統資料夾，輸入`cd /d %windir%\system32`，然後取消註冊該元件輸入`regsvr32 /u VB6Hello.dll`。 您可以再重新註冊輸入`regsvr32 VB6Hello.dll`。  
  
 最後一個步驟是發行應用程式使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>若要發行應用程式更新與隔離的 COM 元件  
  
1.  從**建置**功能表上，按一下 **發行 RegFreeComDemo**。  
  
     [發行精靈] 隨即出現。  
  
2.  在 [發行精靈] 中，指定可以存取並檢查已發行的檔案的本機電腦的磁碟上的位置。  
  
3.  按一下**完成**發行應用程式。  
  
 如果您檢查已發行的檔案，您會注意 sysmon.ocx 檔案是否包含。 控制項是控制項的完全隔離到此應用程式，這表示，如果終端使用者電腦上有另一個應用程式使用不同版本，也不會妨礙與這個應用程式。  
  
## <a name="referencing-native-assemblies"></a>參考原生組件  
 Visual Studio 支援原生的 Visual Basic 6.0 或 c + + 組件; 的參考原生參考時，會呼叫這類的參考。 您可以分辨是否參考為原生藉由確認其**檔案類型**屬性設定為**原生**或**ActiveX**。  
  
 若要加入原生參考，請使用**加入參考**命令，然後瀏覽至資訊清單。 部分元件會將 DLL 內部資訊清單。 在此情況下，您可選擇該 DLL 本身和 Visual Studio 會將它加入做為原生參考如果它偵測到元件包含內嵌的資訊清單。 任何相依的檔案或組件資訊清單中所列，如果它們是在相同的資料夾所參考的元件，也會自動將包含 visual Studio。  
  
 COM 控制項隔離可讓您更容易部署還沒有資訊清單的 COM 元件。 不過，如果元件提供使用資訊清單中，您可以直接參考資訊清單。 事實上，您應該一律使用只要做得到，而不是使用由元件作者所提供的資訊清單**隔離**屬性。  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>免註冊 COM 元件部署的限制  
 免註冊 COM 提供明顯的優點，透過傳統部署技術。 不過，有一些限制和也必須指出的注意事項。最大限制是，它只適用於 Windows xp SP2 或更新版本。 免註冊的 COM 實作所需的核心作業系統中載入元件的方式的變更。 很遺憾，目前沒有下層支援的層免註冊 com。  
  
 不是每個元件是適合使用免註冊 com。 如果下列任何一項成立，就不適當的元件：  
  
-   元件為跨處理序伺服器。 不支援 EXE 伺服器;支援只 Dll。  
  
-   元件所屬的作業系統，或為系統元件，例如 XML、 Internet Explorer 或 Microsoft Data Access Components (MDAC)。 您應該遵循元件作者; 轉散發原則請洽詢您的廠商。  
  
-   元件是應用程式，例如 Microsoft Office 的一部分。 例如，您不應嘗試找出 Microsoft Excel 物件模型。 這是 Office 的一部分，僅能在電腦上的完整安裝 Office 產品時。  
  
-   元件被為了以作為增益集或嵌入式管理單元，例如 Office 增益集或網頁瀏覽器中的控制項。 這類元件通常需要某種超出範圍的資訊清單本身的裝載環境所定義的登錄配置。  
  
-   元件會管理系統，例如，列印多工緩衝處理器的裝置驅動程式的實體或虛擬裝置。  
  
-   資料存取可轉散發套件的元件。 資料應用程式通常需要個別的資料存取可轉散發套件會安裝它們才能執行。 您不應該嘗試隔離的元件，例如 Microsoft ADO 資料控制項、 Microsoft OLE DB 或 Microsoft Data Access Components (MDAC)。 相反地，如果您的應用程式使用 MDAC 或 SQL Server Express，您應該將它們設定為必要條件。請參閱[How to： 使用 ClickOnce 應用程式的安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。  
  
 在某些情況下，它可能會重新設計免註冊 COM 元件的開發人員 如果不可行，仍可以建立及發行應用程式相依於這些透過使用啟動載入器的標準註冊配置。 如需詳細資訊，請參閱[建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。  
  
 COM 元件只能是一次隔離，每個應用程式。 例如，您無法分辨出相同的 COM 元件，從兩個不同**類別庫**屬於相同的應用程式的專案。 這樣會導致建置警告，和應用程式將無法在執行階段載入。 若要避免這個問題，Microsoft 建議您將封裝的單一類別庫中的 COM 元件。  
  
 即使應用程式的部署不需要註冊，則需要有數種案例中的 COM 開發人員在電腦，必須註冊。 `Isolated`屬性需要開發人員的電腦上註冊 COM 元件，以自動產生資訊清單在建置期間。 沒有註冊擷取功能，可以在建置期間叫用自我登錄。 此外，任何未明確定義類型程式庫中的類別不會反映在資訊清單中。 當使用預先存在的資訊清單，例如原生參考的 COM 元件，元件可能不需要註冊在開發階段。 不過，如果就需要註冊元件是一個 ActiveX 控制項，而且您想要將它併入**工具箱**和 Windows Form 設計工具。  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)