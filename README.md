echo "# argocd-deployment" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/kundanvrs/argocd-deployment.git
git push -u origin master
