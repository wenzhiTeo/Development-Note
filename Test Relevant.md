# related docker command
docker-compose -f docker-compose.test.yml up -d --build <br />
docker-compose -f docker-compose.test.yml run web bash run_test.sh <br />

# run specific test
pipenv run python manage.py shell  <br />
pipenv run pytest -k "test..." --reuse-db  <br />

# run forever 
while true; do **python setup.py test** ; done

# run 5 times
for i in {1..5}; do **python setup.py test** ; done
