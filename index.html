// api/ai.js  — Vercel Serverless Function
// Anthropic APIキーをサーバー側で管理し、クライアントに露出させない
//
// 使い方：
// 1. Vercel Dashboard > Settings > Environment Variables に
//    ANTHROPIC_API_KEY を追加する
// 2. このファイルをプロジェクトの /api/ai.js に置く
// 3. hawaii_planner.html と同じリポジトリにデプロイする

export default async function handler(req, res) {
  // POST のみ許可
  if (req.method !== 'POST') {
    return res.status(405).json({ error: 'Method not allowed' });
  }

  const apiKey = process.env.ANTHROPIC_API_KEY;
  if (!apiKey) {
    return res.status(500).json({ error: 'API key not configured' });
  }

  const { system, userMsg, maxTokens = 512 } = req.body;
  if (!userMsg) {
    return res.status(400).json({ error: 'userMsg is required' });
  }

  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': apiKey,
        'anthropic-version': '2023-06-01',
      },
      body: JSON.stringify({
        model: 'claude-haiku-4-5',
        max_tokens: Math.min(maxTokens, 1024), // 上限を念のため制限
        system: system || '',
        messages: [{ role: 'user', content: userMsg }],
      }),
    });

    const data = await response.json();

    if (!response.ok) {
      console.error('Anthropic API error:', data);
      return res.status(response.status).json({ error: data?.error?.message || 'API error' });
    }

    const text = data?.content?.[0]?.text || '';
    return res.status(200).json({ text });

  } catch (err) {
    console.error('Server error:', err);
    return res.status(500).json({ error: 'Internal server error' });
  }
}
