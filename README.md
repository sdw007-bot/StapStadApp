# StapStadApp

import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { AlertCircle, MapPin, PhoneCall, ArrowRight } from "lucide-react";
import { motion } from "framer-motion";

export default function StapStadApp() {
  const [step, setStep] = useState(0);
  const steps = [
    "Begin stap! Loop reguit vir 20m.",
    "Draai links by die verkeerslig. (Nie in die pad nie!)",
    "Hou aan stap. Moenie met die posbus gesels nie!",
    "Jy is amper daar! Moenie nou in ‘n bos slaap nie!",
    "Welkom tuis! Jy het dit gemaak sonder drama!"
  ];

  const [warning, setWarning] = useState("");

  const handleNextStep = () => {
    if (step < steps.length - 1) {
      setStep(step + 1);
    } else {
      setWarning("Jy's veilig tuis! Lekker slaap (en drink water). 💤");
    }
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-blue-100 p-4">
      <Card className="w-full max-w-md p-4 shadow-lg bg-white text-center">
        <CardContent>
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }}>
            <h1 className="text-2xl font-bold mb-2">StapStad 🚶‍♂️</h1>
            <p className="text-lg mb-4">{steps[step]}</p>
            <Button onClick={handleNextStep} className="w-full flex items-center gap-2">
              Volgende stap <ArrowRight size={18} />
            </Button>
            {warning && (
              <div className="mt-4 text-red-500 flex items-center gap-2">
                <AlertCircle size={18} /> {warning}
              </div>
            )}
          </motion.div>
        </CardContent>
      </Card>
    </div>
  );
}
