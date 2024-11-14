pipeline {
    agent any
    parameters {
        string(name: 'Nombre: ', defaultValue: '', description: 'Ingrese nombre del usuario ')
        string(name: 'Apellido: ', defaultValue: '', description: 'Ingresa el apellido del usuario ')
        text(name: 'Observaciones', defaultValue: '', description: 'Ingrese información relevante del usuario')
        booleanParam(name: 'sudo: ', defaultValue: false, description: 'Marque la casilla si el usuario tendrá permisos de usuario sudo')
        choice(name: 'Departamento: ', choices: ['Contabilidad', 'Finanzas', 'Tecnología'], description: 'Elija departamento ')
        password(name: 'Contraseña:', defaultValue: '', description: 'Ingrese la contraseña inicial')
    }
    environment {
        // Variables de entorno
        ENV_VAR = 'Hola, mundo!!!'
    }
    stages {
        stage('Input') {
            steps {
                script {
                    // Los parametros pueden ser accedidos mediante params.parameterName
                    echo "Hola, ${params.name}! Tienes ${params.age} de edad."
                }
            }
        }
    }
}