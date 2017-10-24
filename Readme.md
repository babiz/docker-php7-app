This is the alpha version of the docker environment. I am working on it to make it optimized and with extra options. 

Copy the .env file and make necessary changes
```bash
cp .env.example .env
```
### Create a fresh Laravel application
```bash
# From directory "your-directory"
# Create a Laravel application

    docker run -it --rm \
        -v $(pwd):/opt \
        -w /opt \
        --network=dockerdev_appnet \
        babish/php \
        composer create-project laravel/laravel www
    
# Install predis package for using redis**   
    docker run -it --rm \
        -v $(pwd)/application:/opt \
        -w /opt \
        --network=dockerdev_appnet \
        php/php \
        composer require predis/predis

# Restart required to ensure
# app files shares correctly
docker-compose restart


# From directory docker-dev set permission
chmod -R o+rw application/bootstrap application/storage

# Run migrations for auth scaffolding
docker run -it --rm \
    -v $(pwd)/application:/opt \
    -w /opt \
    --network=dockerdev_appnet \
    babish/php \
    php artisan migrate
```
