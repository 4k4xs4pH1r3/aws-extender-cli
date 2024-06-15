pkgname=aws-extender-cli
pkgver=1.1.3
pkgrel=3
pkgdesc="AWS Extender CLI is a command-line script to test S3 buckets as well as Google Storage buckets and Azure Storage containers for common misconfiguration issues using the boto/boto3 SDK library."
arch=('any')
url="https://github.com/VirtueSecurity/aws-extender-cli/"
license=('GPL')
makedepends=('python')
depends=("python" "python-boto3" "python-botocore")
source=(
  "aws_extender_cli.py"
)
sha256sums=('cad281be610bd6c1d6d11f35c70d455a8a416bd92b181578602997572408df61')

prepare() {
  chmod +x aws_extender_cli.py
}

package() {
  # Install Pip Dependencies and Create the directory for the binary
  pip install boto3 botocore
  mkdir -p $pkgdir/usr/local/bin

  # Install the script with its new name if you renamed it
  install -Dm755 aws_extender_cli.py $pkgdir/usr/local/bin/aws-extender-cli
}

# Add the final step to run "aws-extender-cli -v" only if the package was updated
post_install() {
  # Check if the package was actually updated, and only then execute the command
  if [[ "$1" == "upgrade" ]]; then
    aws-extender-cli -v
  fi
}
