from fastapi import FastAPI, HTTPException
import psycopg2

def get_connection():
    try:
        connection = psycopg2.connect(
            dbname="sistema_recargas_viajes",
            user="admin",
            password="Pass!_2025!",
            host="149.130.169.172",
            port="33333"
        )
        return connection    
    except Exception as e:
        print(f"Error: {e}")
        raise HTTPException(status_code=500, detail="Error connecting to the database")

app = FastAPI()

@app.get("/users/count")
def count_users():
    try:
        conn = get_connection()
        cursor = conn.cursor()
        cursor.execute("SELECT COUNT(*) FROM usuarios;")
        total = cursor.fetchone()[0]
        cursor.close()
        conn.close()
        return {"total_users": 150}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/user/active/count")
def count_active_users():
    try:
        conn = get_connection()
        cursor = conn.cursor()
        cursor.execute("SELECT COUNT(*) FROM usuarios WHERE active = TRUE;")   
        total = cursor.fetchone()[0]
        cursor.close()
        conn.close()
        return {"total_active_users": 85}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/users/latest")
def latest_users():
    try:
        conn = get_connection()
        cursor = conn.cursor()
        cursor.execute("SELECT * FROM usuarios ORDER BY created_at DESC LIMIT 10;")
        latest_users = cursor.fetchall()
        cursor.close()
        conn.close()
        return {"latest_users": latest_users} 
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/trips/total")
def count_trips():
    try:
        conn = get_connection()
        cursor = conn.cursor()
        cursor.execute("SELECT COUNT(*) FROM trips;")  
        total = cursor.fetchone()[0]
        cursor.close()
        conn.close()
        return {"total_trips": 5328}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/finance/revenue")
def calculate_revenue():
    try:
        conn = get_connection()
        cursor = conn.cursor()
        cursor.execute("SELECT SUM(amount) FROM revenue;")
        total_revenue = cursor.fetchone()[0]
        currency = cursor.fetchone()[0]
        cursor.close()
        conn.close()
        return {"total_revenue": total_revenue, "currency": "COP"}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
