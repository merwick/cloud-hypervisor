stage ("Builds") {
	node ('bionic') {
		stage ('Checkout') {
			checkout scm
		}
		stage ('Install system packages') {
			sh "sudo DEBIAN_FRONTEND=noninteractive apt-get install -yq build-essential mtools libssl-dev pkg-config"
			sh "sudo apt-get install -yq flex bison libelf-dev qemu-utils"
		}
		stage ('Install Rust') {
			sh "nohup curl https://sh.rustup.rs -sSf | sh -s -- -y"
		}
		stage ('Run integration tests') {
			sh "sudo chmod a+rw /dev/kvm"
			sh "scripts/run_integration_tests.sh"
		}
	}
}
