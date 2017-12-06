---
title: "Segurança de associação personalizada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: "30"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 943a56095707efdba0e20c40b2c96e24e8fd4ea3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-security"></a><span data-ttu-id="06452-102">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="06452-102">Custom Binding Security</span></span>
<span data-ttu-id="06452-103">Este exemplo demonstra como configurar a segurança por meio de uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="06452-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="06452-104">Ele mostra como usar uma associação personalizada para habilitar a segurança em nível de mensagem junto com um transporte seguro.</span><span class="sxs-lookup"><span data-stu-id="06452-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="06452-105">Isso é útil quando um transporte seguro é necessária para transmitir mensagens entre cliente e serviço e simultaneamente as mensagens devem ser seguras no nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="06452-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="06452-106">Essa configuração não é suportada por associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="06452-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="06452-107">Este exemplo consiste em um programa de console de cliente (EXE) e um programa de console de serviço (EXE).</span><span class="sxs-lookup"><span data-stu-id="06452-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="06452-108">O serviço implementa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="06452-108">The service implements a duplex contract.</span></span> <span data-ttu-id="06452-109">O contrato é definido pelo `ICalculatorDuplex` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="06452-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="06452-110">O `ICalculatorDuplex` interface permite que o cliente executar operações matemáticas, calcular um resultado em execução em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="06452-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="06452-111">Independentemente, o serviço pode retornar resultados no `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="06452-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="06452-112">Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens sendo enviadas entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="06452-113">Uma associação personalizada é definida que oferece suporte à comunicação duplex e seguro.</span><span class="sxs-lookup"><span data-stu-id="06452-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06452-114">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="06452-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="06452-115">A configuração do serviço define uma associação personalizada que suporta o seguinte:</span><span class="sxs-lookup"><span data-stu-id="06452-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="06452-116">Comunicação TCP protegida usando o protocolo TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="06452-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="06452-117">Segurança de mensagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="06452-117">Windows message security.</span></span>  
  
 <span data-ttu-id="06452-118">A configuração de associação personalizada permite que o transporte seguro, simultaneamente, permitindo a segurança no nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="06452-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="06452-119">A ordenação dos elementos de associação é importante definir uma associação personalizada, como cada uma representa uma camada da pilha de canal (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="06452-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="06452-120">A associação personalizada é definida nos arquivos de configuração do cliente e de serviço, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="06452-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="06452-121">A associação personalizada usa um certificado de serviço para autenticar o serviço no nível do transporte e proteger as mensagens durante a transmissão entre cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="06452-122">Isso é feito usando o `sslStreamSecurity` elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="06452-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="06452-123">Certificado do serviço é configurado usando um comportamento de serviço, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="06452-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="06452-124">Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows - esse é o tipo de credencial padrão.</span><span class="sxs-lookup"><span data-stu-id="06452-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="06452-125">Isso é feito usando o `security` elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="06452-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="06452-126">Cliente e serviço são autenticados usando a segurança de nível de mensagem se o mecanismo de autenticação Kerberos está disponível.</span><span class="sxs-lookup"><span data-stu-id="06452-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="06452-127">Isso ocorre se o exemplo é executado no ambiente do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="06452-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="06452-128">Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM é usada.</span><span class="sxs-lookup"><span data-stu-id="06452-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="06452-129">NTLM autentica o cliente para o serviço, mas não autenticar o serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="06452-130">O `security` elemento de associação está configurado para usar `SecureConversation``authenticationType`, que resulta na criação de uma sessão de segurança no cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="06452-131">Isso é necessário para habilitar o contrato do serviço duplex trabalhar.</span><span class="sxs-lookup"><span data-stu-id="06452-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="06452-132">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="06452-133">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="06452-134">Quando você executar o exemplo, você ver as mensagens retornadas ao cliente sobre a interface de retorno de chamada enviada do serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="06452-135">Cada resultado intermediário é exibido, seguido por toda a equação após a conclusão de todas as operações.</span><span class="sxs-lookup"><span data-stu-id="06452-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="06452-136">Pressione ENTER para fechar o cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="06452-137">O arquivo bat incluído permite que você configure o cliente e o servidor com o certificado de serviço relevantes para executar um aplicativo hospedado que exige a segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="06452-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="06452-138">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="06452-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="06452-139">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote que se aplicam a este exemplo, para que eles podem ser modificados para executar a configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="06452-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="06452-140">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="06452-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="06452-141">As seguintes linhas do arquivo bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="06452-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="06452-142">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="06452-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="06452-143">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="06452-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="06452-144">Esse arquivo em lote padrão é o nome do servidor com o localhost.</span><span class="sxs-lookup"><span data-stu-id="06452-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="06452-145">O certificado é armazenado no repositório de CurrentUser para os serviços Web hospedados.</span><span class="sxs-lookup"><span data-stu-id="06452-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="06452-146">Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="06452-147">Armazenam as linhas a seguir na cópia de arquivo bat o certificado do servidor em que as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="06452-148">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="06452-149">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="06452-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="06452-150">O arquivo em lotes bat é projetado para ser executado de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="06452-151">Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="06452-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="06452-152">Essa variável de ambiente é definida automaticamente dentro de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06452-153">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="06452-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06452-154">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06452-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06452-155">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06452-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="06452-156">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06452-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="06452-157">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="06452-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="06452-158">Abra uma janela de Prompt de comando do Visual Studio com privilégios de administrador e execute bat da pasta de instalação do exemplo.</span><span class="sxs-lookup"><span data-stu-id="06452-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="06452-159">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="06452-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06452-160">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="06452-161">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="06452-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="06452-162">Inicie Service.exe de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="06452-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="06452-163">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="06452-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="06452-164">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="06452-165">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="06452-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="06452-166">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="06452-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="06452-167">No computador do serviço:</span><span class="sxs-lookup"><span data-stu-id="06452-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="06452-168">Crie um diretório virtual chamado servicemodelsamples no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="06452-169">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="06452-170">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="06452-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="06452-171">Copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="06452-172">Execute o seguinte comando em um prompt de comando do Visual Studio é aberto com privilégios de administrador: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="06452-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="06452-173">Isso cria o certificado de serviço com o nome de entidade correspondente ao nome do computador em que o arquivo em lotes foi executado no.</span><span class="sxs-lookup"><span data-stu-id="06452-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="06452-174">O arquivo em lotes bat é projetado para ser executado de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="06452-175">Isso requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="06452-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="06452-176">Essa variável de ambiente é definida automaticamente dentro de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="06452-177">Alterar o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) dentro do arquivo Service.exe.config para refletir o nome da entidade do certificado gerado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="06452-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="06452-178">Execute Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="06452-179">No computador cliente:</span><span class="sxs-lookup"><span data-stu-id="06452-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="06452-180">Copie os arquivos de programa do cliente da pasta \client\bin\ no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="06452-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="06452-181">Também copie o arquivo Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="06452-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="06452-182">Execute Cleanup.bat para remover quaisquer certificados antigos de exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="06452-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="06452-183">Exportar o certificado do serviço de abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador de serviço (substitua `%SERVER_NAME%` com o nome totalmente qualificado do computador onde o serviço está executando):</span><span class="sxs-lookup"><span data-stu-id="06452-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="06452-184">Copie %SERVER_NAME%.cer para o computador cliente (substituto SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está sendo executado).</span><span class="sxs-lookup"><span data-stu-id="06452-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="06452-185">Importar o certificado do serviço abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador cliente (substituto SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está executando):</span><span class="sxs-lookup"><span data-stu-id="06452-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="06452-186">Etapas c, d e e não são necessárias se o certificado é emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="06452-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="06452-187">Modifique o arquivo do cliente App. config da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="06452-187">Modify the client’s App.config file as follows:</span></span>  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  <span data-ttu-id="06452-188">Se o serviço é executado sob uma conta que não seja o NetworkService ou LocalSystem em um ambiente de domínio, você talvez precise modificar a identidade do ponto de extremidade para o ponto de extremidade de serviço no arquivo App. config do cliente, para definir o UPN ou o SPN com base em apropriado a conta que é usado para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="06452-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="06452-189">Para obter mais informações sobre a identidade do ponto de extremidade, consulte o [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="06452-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="06452-190">Execute Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="06452-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="06452-191">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="06452-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="06452-192">Execute Cleanup.bat na pasta exemplos depois de terminar de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="06452-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06452-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06452-193">See Also</span></span>