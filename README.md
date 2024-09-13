Este guia descreve o processo completo para configurar e fazer o deploy de uma aplicação Laravel 11 na Railway. Siga os passos abaixo.

### No arquivo app/Providers/AppServiceProvider.php:

```
public function boot(): void
{
    if (app()->environment('production')) {
        URL::forceScheme('https');
    }
}
```

### Passos no Railway:

- Criar uma conta e vincular o Github;
- Criar um projeto;
- Criar o serviço de banco de dados;
- Criar o serviço da aplicação a partir do repositório do projeto;
- Acessar as configurações do serviço da aplicação e configurar as variáveis de ambiente;
    - Usando o "Raw Editor", pode copiar e colar os dados do arquivo .env do ambiente de desenvolvimento;
    - Alterar APP_ENV para "production" e APP_DEBUG para "false";
    - Configurar as variáveis de conexão com o banco de dados;
    - Criar a variável NIXPACKS_BUILD_CMD (ver abaixo).
- Executar o deploy.

Seria possível incluir o comando de migração e de seeding.
  
```
NIXPACKS_BUILD_CMD="composer install && npm install && npm run build && php artisan optimize && php artisan storage:link"
```


