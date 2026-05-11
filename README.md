from abc import ABC, abstractmethod
from datetime import datetime
import logging

# ==========================================================
# CONFIGURACIÓN DE LOGS
# ==========================================================

logging.basicConfig(
    filename="software_fj.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)
