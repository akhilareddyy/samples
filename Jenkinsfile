pipeline{
    agent any

stages{
 stage('Checkout repo') {
    steps {
      git url: 'https://github.com/akhilareddyy/samples.git', branch: 'main', credentialsId: '49571fd3-6bdc-4181-9a6f-2bb4f20d5a22'
     }
  }


stage('Restore packages'){
   steps{
      sh "dotnet restore ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj"
     }
  }


stage('Build'){
   steps{
      sh "dotnet build ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj --configuration Release"
    }
 }

stage('Publish'){
     steps{
       sh "dotnet publish ./samples/aspnetcore/blazor/BinarySubmit/BinarySubmit.csproj "
     }
}
        
stage('Deploy to Azure (DEV)') {
	steps {
	  azureWebAppPublish azureCredentialsId: "25b385e8-d841-4c5c-a422-6ec2b07e3af9", 
	  resourceGroup: "app-mig-rg", 
	  appName: "appmig1105-wapp", 
	  sourceDirectory: "samples/aspnetcore/blazor/BinarySubmit/"
      }
}

}
}
