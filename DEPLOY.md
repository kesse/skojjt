Deploy

cd default
git pull origin master
gcloud app deploy app.yaml --project gotalejon-narvaro



// dev run
dev_appserver.py $PWD


Update database indexes

gcloud datastore indexes create ./index.yaml
