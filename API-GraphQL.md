# API GraphQL

## Descripción

GraphQL es un lenguaje de consulta y manipulación de datos desarrollador por Facebook que permite a los clientes solicitar solo los datos que necesitan, lo que puede reducir la sobrecarga de red y mejorar el rendimiento de las aplicaciones. En Laravel, puedes implementar GraphQL utilizando paquetes como 'lighthouse-php', que te permite definir tu esquema GraphQL y manejar las consultas GraphQL en tu aplicación Laravel.

## Características

* Permite a los clientes especificar la estructura exacta de los datos que desean en una sola solicitud.
* Proporciona un esquema flexible que puedes definir según las necesidades de tu aplicación.
* Permite la validación de consultas GraphQL pra evitar consultas mal formadas o incorrectas.

## Pasos para implementar una API GraphQL en Laravel

1. Instalar paquete Lighthouse: Utiliza Composer para instalar el paquete 'lighthouse-php' en tu proyecto Laravel.
        
        composer require nuwave/lighthouse

2. Publicar configuración: Utiliza el comando artisan para publicar la configuración de Lighthouse en tu proyecto.

        php artisan vendor:publish --tag=lighthouse-schema

3. Definir esquema GraphQL: Define tu esquema GraphQL en el archivo 'graphql/schema.graphql'.
   
##### Type


        "Post in the application."
        type Post {
            "Unique primary key."
            id: ID!

            "Title of the post."
            title: String!

            "Content of the post."
            content: String!

            "When the post was created."
            created_at: DateTime!

            "When the post was last updated."
            updated_at: DateTime!
        }

##### Query

        "Indicates what fields are available at the top level of a query operation."
        type Query {
            "Find a single post by an identifying attribute."
            post("Search by primary key." id: ID @eq): Post @find

            "List multiple posts."
            posts: [Post!]! @paginate(defaultCount: 10)
        }

##### Mutation

        type Mutation {
                createPost(
                        "Title of the post."
                        title: String! @rules(apply: ["required"])

                        "Content of the post."
                        content: String! @rules(apply: ["required"])
                ): Post @create

                updatePost(
                        "Unique primary key."
                        id: ID! @eq @rules(apply: ["required"])

                        "Title of the post."
                        title: String @rules(apply: ["required"])

                        "Content of the post."
                        content: String @rules(apply: ["required"])
                ): Post @update

                deletePost(id: ID! @whereKey): Post! @delete
        }


## Ejemplos de consultas y mutaciones GraphQL para CRUD

### Crear un post

#### Consulta

        mutation CreatePost($title: String!, $content: String!) {
                createPost(title: $title, content: $content) {
                        id
                        title
                        content
                }
        }

#### Variables

        {
        "title": "Título del nuevo post",
        "content": "Contenido del nuevo post"
        }

#### Respuesta 

        {
                "data": {
                        "createPost": {
                        "id": "1",
                        "title": "Título del nuevo post",
                        "content": "Contenido del nuevo post"
                        }
                }
        }






