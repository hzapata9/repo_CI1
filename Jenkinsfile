pipeline { 
    agent any 
    environment { 
        NODE_VERSION = '23' // Cambia si usas otra versión de Node.js 
    } 
 
    stages { 
        stage('Checkout') { 
            steps { 
                echo "📥 Clonando el repositorio..." 
                checkout scm 
            } 
        }
        stage('Install') { 
            steps { 
                script { 
                    try { 
                        echo "⚙️ Instalando dependencias..." 
                        sh 'whoami'
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de Install") 
                    } 
                } 
            } 
        } 
 
        stage('Build') { 
            steps { 
                script { 
                    try { 
                        echo "⚙️ Haciendo Build..." 
                        sh 'npm run build' 
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de Build") 
                    } 
                } 
            } 
        } 

        stage('Test') { 
            steps { 
                script { 
                    try { 
                        echo "🧪 Ejecutando pruebas..." 
                        sh 'npm run test' 
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de Test") 
                    } 
                } 
            } 
        } 
 
        stage('Deploy') { 
            steps { 
                script { 
                    try { 
                        echo "🚀 Desplegando aplicación..." 
                        sh 'npm start &' 
                    } catch (Exception e) { 
                        error("❌ Error en la etapa de Deploy") 
                    } 
                } 
            } 
        } 
    } 
 
    post { 
        success { 
            echo "✅ Pipeline completado con éxito" 
        } 
        failure { 
            echo "❌ El pipeline ha fallado" 
        } 
    } 
}