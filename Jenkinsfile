pipeline{
    agent any

stages{
 stage('Checkout') {
    steps {
      git url: 'https://github.com/akhilareddyy/samples.git', branch: 'main', credentialsId: ''
     }
  }


stage('Restore packages'){
   steps{
      bat "dotnet restore ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj"
     }
  }


stage('Build'){
   steps{
      bat "dotnet build ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj --configuration Release"
    }
 }

stage('Publish'){
     steps{
       bat "dotnet publish ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj "
     }
}


        
stage('Deploy to Azure (DEV)') {
	steps {
		azureWebAppPublish azureCredentialsId: "", 
		resourceGroup: "app-mig-rg", 
		appName: "appmig1105-wapp", 
		sourceDirectory: "samples/aspnetcore/blazor/BinarySubmit/"
	}
}


}
 } 
  
