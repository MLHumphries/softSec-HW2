node('appserver_softsec')
{
	def app
	stage('Cloning Git')
	{
		//Checks for repo
		checkout scm
	}

	stage('Build-and-Tag')
	{
		//Builds image. Same as docker build on command line
		app = docker.build('mlhumphries/hw2')
	}

	stage('Post-to-DockerHub')
	{
		
		docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials1')
		{
			app.push('latest')
		}
	}

	stage('Deploy')
	{
		
		sh "docker-compose down"
		sh "docker-compose up -d"
	}

}