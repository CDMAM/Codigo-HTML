import React, { useState } from "react";
import Header from "@/components/Header";
import FileUpload from "@/components/FileUpload";
import DataTable from "@/components/DataTable";
import DataSummary from "@/components/DataSummary";
import PredictionModels from "@/components/PredictionModels";

const Index = () => {
  const [data, setData] = useState<any[] | null>(null);

  const handleFileUploaded = (uploadedData: any) => {
    setData(uploadedData);
  };

  return (
    <div className="min-h-screen bg-gray-50">
      <Header />
      
      <main className="container mx-auto py-8 px-4">
        <section className="mb-12">
          <h2 className="text-3xl font-bold text-medical-800 mb-6">
            Sistema Predictivo de Asma
          </h2>
          <p className="text-lg text-gray-600 mb-8 max-w-3xl">
            Esta herramienta permite analizar datos de pacientes con asma y generar modelos predictivos 
            para ayudar en el diagnóstico y tratamiento. Cargue un archivo Excel con datos de pacientes 
            para comenzar.
          </p>

          <FileUpload onFileUploaded={handleFileUploaded} />
        </section>

        {data && (
          <>
            <section className="mb-12">
              <h2 className="text-2xl font-bold text-medical-800 mb-6">
                Análisis Exploratorio de Datos
              </h2>
              
              <DataSummary data={data} />
              <DataTable data={data} />
            </section>

            <section className="mb-12">
              <h2 className="text-2xl font-bold text-medical-800 mb-6">
                Modelos Predictivos
              </h2>
              
              <PredictionModels data={data} />
            </section>
          </>
        )}

        <section className="mt-16 py-8 border-t border-gray-200" id="reports">
          <h2 className="text-2xl font-bold text-medical-800 mb-4">
            Acerca del Sistema Predictivo
          </h2>
          <div className="grid md:grid-cols-2 gap-8">
            <div>
              <h3 className="text-xl font-medium text-medical-700 mb-2">Modelos Implementados</h3>
              <p className="text-gray-600 mb-4">
                El sistema utiliza algoritmos avanzados de Machine Learning similares a los implementados en Weka:
              </p>
              <ul className="list-disc list-inside space-y-1 text-gray-600">
                <li>Random Forest (Bosques aleatorios)</li>
                <li>SVM (Máquinas de vectores de soporte)</li>
                <li>Logistic Regression (Regresión logística)</li>
                <li>Neural Networks (Redes neuronales)</li>
                <li>Decision Trees (Árboles de decisión)</li>
              </ul>
            </div>
            <div>
              <h3 className="text-xl font-medium text-medical-700 mb-2">Funcionalidades</h3>
              <ul className="list-disc list-inside space-y-1 text-gray-600">
                <li>Carga de archivos Excel con datos de pacientes</li>
                <li>Visualización de datos mediante gráficos interactivos</li>
                <li>Ejecución de múltiples modelos predictivos</li>
                <li>Comparación del rendimiento entre modelos</li>
                <li>Generación de informes en PDF</li>
              </ul>
            </div>
          </div>
        </section>
      </main>

      <footer className="bg-medical-800 text-white py-8">
        <div className="container mx-auto px-4">
          <p className="text-center">© 2025 AsmaPredict - Sistema Predictivo para Asma</p>
        </div>
      </footer>
    </div>
  );
};

export default Index;
